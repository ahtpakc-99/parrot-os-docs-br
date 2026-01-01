```markdown
# Criando um USB Bootável (Live USB)

Antes de tudo, você precisa baixar o arquivo ISO mais recente em nosso [site oficial](https://parrotsec.org/download/).

Em seguida, você deve gravar a ISO em um pendrive usando **Balena Etcher**, **ROSA ImageWriter** ou **Rufus**.
* **Balena Etcher e ROSA ImageWriter:** Funcionam em Linux, macOS e Windows.
* **Rufus:** Disponível apenas para Windows (8 ou superior).

Para usuários de **Linux ou macOS**, recomendamos usar o **Etcher**, mas você também pode usar a ferramenta de linha de comando **DD** se preferir.
Para usuários de **Windows**, recomendamos usar o **Etcher** ou **Rufus**.

## ⚠️ Aviso Importante: Padrão ISOHybrid
O arquivo `.iso` do Parrot usa o **padrão ISO 9660** (também conhecido como ISOHybrid). É um formato especial que contém não apenas o conteúdo da partição, mas também a tabela de partição.

Alguns programas de gravação de ISO não escrevem a ISO bit-a-bit na unidade USB em baixo nível. Eles criam uma tabela de partição personalizada e apenas copiam os arquivos para o USB de uma maneira não oficial e não padrão. Esse comportamento vai contra o propósito do ISOHybrid e pode **quebrar funcionalidades do sistema** ou tornar a instalação impossível.

> **NÃO USE:** É **altamente recomendado** que você **não use Unetbootin**, Universal USB Installer ou qualquer programa que não seja compatível com ISOHybrid.

### Requisitos de Hardware
Você precisará de um pendrive com tamanho mínimo de:
* **8 GB** para a Security Edition.
* **4 GB** para a Home Edition.

---

## Ferramenta 1: Balena Etcher (Recomendado)
*Disponível para Windows, macOS e Linux.*

1.  Conecte seu pendrive na porta USB.
2.  Baixe e execute o [Balena Etcher](https://balena.io/etcher). (No Linux, baixe e clique no arquivo `.AppImage`).
3.  Clique em **Flash from file** (Flash a partir de arquivo).
4.  Selecione a ISO do Parrot e verifique se o pendrive selecionado para gravação é o correto.
5.  Clique em **Flash!** e o processo de formatação iniciará.
6.  Assim que a gravação terminar, você pode usar o pendrive para dar boot no seu computador.

---

## Ferramenta 2: Linha de Comando DD (Avançado)
*Nativo em sistemas Linux e macOS.*

O `dd` (e seus derivados) é uma ferramenta integrada em todos os sistemas UNIX e UNIX-like, usada para escrever arquivos bit a bit.

> **Cuidado:** Devido ao potencial de **danificar seu sistema** (se você selecionar o disco errado), se você não estiver familiarizado com Linux, recomendamos fortemente usar o Etcher.

**Comando:**
```bash
sudo dd status=progress if=Parrot-<edicao>-<versao>_amd64.iso of=/dev/sdX

```

*(Substitua `/dev/sdX` pela letra correta do seu pendrive, ex: `/dev/sdb`. Não use o número da partição como `/dev/sdb1`).*

---

## Ferramenta 3: ROSA Image Writer

*Disponível para Windows, macOS e Linux.*

Outra ferramenta confiável.

1. Baixe-o do site oficial e extraia os arquivos.
2. Execute o `RosaImageWriter`.
3. Selecione a imagem **ISO** e o dispositivo **USB**.
4. Clique em **Write** (Escrever) e aguarde o término.

---

## Ferramenta 4: Rufus

*Disponível apenas para Windows.*

Para quem usa Windows 8 ou superior, o Rufus é uma excelente alternativa, desde que configurado corretamente. Não requer instalação.

1. Baixe o executável do site do Rufus e abra-o.
2. Selecione seu pendrive no menu **Dispositivo**.
3. Selecione a ISO do Parrot no menu **Seleção de Boot**.
4. Clique em **INICIAR**.
5. **IMPORTANTE:** Quando perguntado, escolha o **Modo DD** (Gravar em modo Imagem DD).
* *Nota: O modo ISO padrão pode causar problemas com imagens ISOHybrid.*


6. Aguarde o processo terminar.
