# Configuração do Ambiente de Desenvolvimento

Este guia detalha como configurar um ambiente de desenvolvimento completo para construir pacotes do Parrot OS. Seguir estes passos instalará as ferramentas essenciais e criará um ambiente **chroot** limpo, garantindo construções (builds) confiáveis e reprodutíveis.

## 1. Configuração Inicial

Este é um processo único que prepara sua máquina para todo o trabalho futuro de empacotamento.

### Passo 1: Atualizar Listas de Pacotes
Sincronize seu índice local para garantir a instalação das versões mais recentes.
```bash
sudo apt update

```

### Passo 2: Instalar Ferramentas de Desenvolvimento

O Parrot utiliza a base de ferramentas do Debian para empacotamento.

```bash
sudo apt install devscripts git-buildpackage sbuild

```

**O que estamos instalando?**

* **devscripts:** Coleção de scripts que automatizam tarefas comuns (como criar changelogs).
* **git-buildpackage:** Ferramenta indispensável para manter pacotes Debian dentro de repositórios Git.
* **sbuild:** O núcleo do processo. Ele constrói pacotes em um ambiente isolado (chroot), garantindo que nada da sua máquina pessoal influencie o pacote final.

### Passo 3: Criar o Chroot de Construção

O chroot é uma cópia minimalista e isolada do sistema. Substitua `<architecture>` pela sua arquitetura alvo (ex: `amd64` ou `arm64`).

```bash
sudo sbuild-createchroot --arch=<architecture> lory /var/lib/sbuild/lory-<architecture>-sbuild [https://deb.parrot.sh/parrot](https://deb.parrot.sh/parrot)

```

### Passo 4: Adicionar Usuário ao Grupo Sbuild

Isso permite que você execute builds sem precisar usar `sudo` o tempo todo. **Você precisará deslogar e logar novamente após este comando.**

```bash
sudo sbuild-adduser $USER

```

---

## 2. Ferramentas Essenciais

Conhecer estas ferramentas melhorará significativamente seu fluxo de trabalho:

### dch (Debian Changelog)

Usado para editar o arquivo `debian/changelog`. É obrigatório para registrar mudanças de versão e correções.

* **Dica:** Rodar `dch -i` cria automaticamente uma nova entrada com a versão incrementada e o timestamp correto.

### uscan & debian/watch

O arquivo `debian/watch` contém regras que ensinam o sistema a procurar novas versões do software original (upstream). Quando você roda o comando `uscan`, ele verifica automaticamente o site do autor (ex: GitHub) e baixa o código novo se houver.

### sbuild

É o padrão profissional. Ele garante que todas as dependências estejam declaradas corretamente no arquivo `control` do pacote. Se faltar uma dependência no seu arquivo, o `sbuild` falhará, evitando o erro clássico de "funciona na minha máquina".

---

## 3. Gerenciando Chroots

### Criando um Chroot

Como mostrado na configuração, você pode ter múltiplos chroots para diferentes arquiteturas.

```bash
sudo sbuild-createchroot --arch=<architecture> lory /var/lib/sbuild/lory-<architecture>-sbuild [https://deb.parrot.sh/parrot](https://deb.parrot.sh/parrot)

```

### Resolução de Problemas: Erro "chroot already exists"

Se você tentar criar um chroot que já foi definido anteriormente, verá um erro de conflito. Para resolver, você deve remover os rastros da configuração antiga manualmente:

1. **Verifique o diretório atual:**
```bash
schroot -i -c lory-<architecture>-sbuild

```


2. **Remova o diretório (Cuidado: comando irreversível):**
```bash
sudo rm -rf /var/lib/sbuild/lory-<architecture>-sbuild

```


3. **Remova a configuração do schroot:**
```bash
sudo rm /etc/schroot/chroot.d/lory-<architecture>-sbuild.conf

```


4. **Remova a configuração do sbuild:**
```bash
sudo rm /etc/sbuild/chroot/lory-<architecture>-sbuild.conf

```

Após estes passos, o sistema estará limpo para que você execute o comando `sbuild-createchroot` novamente com sucesso.
