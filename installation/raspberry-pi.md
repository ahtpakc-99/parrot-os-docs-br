# Instalação no Raspberry Pi

O ParrotOS está disponível para arquitetura ARM em todas as variantes oferecidas: **Core**, **Home** e **Security**.

Isso permite transformar seu Raspberry Pi em uma estação de hacking portátil (excelente para *Dropboxes* físicos) ou um desktop leve.

## Requisitos
Para prosseguir com a instalação, você precisará de um cartão microSD de pelo menos **8 GB**.
* *Nota:* A edição Core (sem interface gráfica) pode ser instalada em um microSD de 4 GB.

> **Compatibilidade:**
> Este procedimento se aplica a qualquer edição do Parrot no Raspberry Pi.
> Atualmente, o ParrotOS foi testado com sucesso nos modelos:
> * Raspberry Pi 3B
> * Raspberry Pi 4B
> * Raspberry Pi 400
> * Raspberry Pi 5

## Processo de Instalação

### 1. Download da Imagem
Baixe a edição do ParrotOS de sua escolha (procure pela seção Raspberry Pi/IoT) no [nosso site](https://www.parrotsec.org/download/).
* O arquivo baixado estará no formato `.img.xz` (comprimido).

### 2. Preparando o Cartão SD
Insira o microSD no seu computador. Você precisará de um software para gravar a imagem. Recomendamos:
* **Raspberry Pi Imager** (Oficial)
* **Balena Etcher**

#### Usando o Raspberry Pi Imager:
1.  Abra o programa.
2.  Clique em **Choose OS** (Escolher SO).
3.  Role a lista até o final e selecione **Use custom** (Usar personalizado).
4.  Uma janela abrirá: selecione o arquivo `.img.xz` do Parrot que você baixou.
5.  Clique em **Choose Storage** (Escolher Armazenamento) e selecione seu cartão microSD.
6.  Clique em **Write** (Escrever).

### 3. Finalizando
O processo de gravação iniciará (pode demorar alguns minutos para gravar e verificar).
* Assim que terminar, remova o microSD do computador.
* Insira-o no seu Raspberry Pi.
* Conecte a energia e o monitor (se houver).

**Divirta-se!** O sistema deve iniciar automaticamente no ambiente do Parrot.

---
Se tiver dúvidas ou problemas, pedimos gentilmente que entre em contato através de nossos canais sociais (Telegram/Discord).
