# Construção de Pacotes

Este guia cobre o processo de construção de um pacote Debian a partir de uma fonte "debianizada", geralmente gerenciada em um repositório Git. O foco está no uso do **sbuild**, essencial para suportar múltiplas arquiteturas (como `arm64`) e garantir a compilação em um ambiente limpo.

> **Dica Importante:** Antes de modificar um pacote, recomenda-se construí-lo em seu estado original. Isso estabelece uma base de comparação e garante que, se surgirem problemas após suas modificações, a causa estará nas suas alterações e não na fonte original ou no ambiente.

---

## 1. Baixar o Tarball da Fonte Original
Antes de construir o pacote Debian, você precisa gerar o tarball da fonte original do autor (ex: `nome-do-pacote_versao.orig.tar.gz`).

A partir da raiz do seu repositório git, execute:
```bash
gbp export-orig --verbose --no-pristine-tar

```

**O que este comando faz?**

* **gbp export-orig:** Extrai o código-fonte do histórico do git (geralmente de uma tag ou branch upstream) e cria o arquivo `.orig.tar.gz` no diretório pai.
* **--no-pristine-tar:** Gera o tarball diretamente da árvore de fontes em vez de depender da branch `pristine-tar`.

---

## 2. Construir o Pacote com sbuild

Com o tarball pronto, podemos proceder para a construção. O comando abaixo demonstra uma **compilação cruzada (cross-compilation)** para a arquitetura `arm64` visando a distribuição "lory" do Parrot OS.

```bash
sbuild --arch=arm64 --dist=lory --apt-update --source --force-orig-source --no-run-lintian --no-clean-source -v --chroot=lory-arm64-sbuild -D .

```

### Entendendo as Flags de Construção:

* **--arch=arm64:** Especifica a arquitetura alvo. O sbuild configurará o ambiente e a variável `$DEB_HOST_ARCH` adequadamente.
* **--dist=lory:** Define a distribuição alvo para que o APT busque as dependências corretas dentro do chroot.
* **--apt-update:** Garante que a lista de pacotes dentro do chroot esteja atualizada antes de começar.
* **--force-orig-source:** Força o uso do arquivo `.orig.tar.gz` que criamos no passo anterior.
* **--no-run-lintian:** Pula o `lintian` (ferramenta que verifica erros de política Debian). Útil para acelerar testes durante o desenvolvimento.
* **--no-clean-source:** Impede que o sbuild limpe a árvore de fontes após terminar. Isso é vital para debugar falhas, pois mantém os arquivos temporários para inspeção.
* **-D . :** Realiza a construção no diretório atual.

Ao final, os arquivos `.deb` e outros arquivos do pacote estarão localizados no **diretório pai**.

---

## 3. Alternativa: Construindo com git-sbuildpkg

Após confirmar que o pacote constrói corretamente manualmente, você pode usar a ferramenta auxiliar do Parrot, o **git-sbuildpkg**. Ela é um "wrapper" que automatiza várias etapas.

### Vantagens do git-sbuildpkg:

1. **Exportação Automática:** Ele executa o equivalente ao `gbp export-orig` para você.
2. **Criação de Ambiente:** Detecta a distribuição correta e pode até criar o `schroot` para a arquitetura desejada se ele ainda não existir.

### Como usar:

A sintaxe básica é: `./main.sh <caminho> <branch> <arquitetura>`.

```bash
cd <pasta_do_git-sbuildpkg>
./main.sh <caminho_do_repositorio_git> debian/latest arm64

```

* Se nenhuma arquitetura for especificada, o padrão será `amd64`.
* O `<caminho>` pode ser uma pasta local ou uma URL remota do repositório.
