# Instalação no UTM (Apple Silicon - Mac)

O Parrot OS também está disponível para ser virtualizado em plataformas Apple com CPUs **M1, M2 e M3** (e suas variantes Pro/Max/Ultra).

Especificamente, o Parrot pode ser usado através do software open source **UTM**. Diferente do VirtualBox (que não roda bem em arquitetura ARM), o UTM oferece desempenho quase nativo para o Parrot.

## 1. Preparação
Antes de começar, você precisa:
1.  Baixar e instalar o [UTM para Mac](https://mac.getutm.app/).
2.  Ao abrir o UTM, você verá uma tela inicial pronta para receber suas máquinas virtuais.

## 2. O Formato .UTM (Método Rápido)
O Parrot fornece aos usuários um arquivo com a extensão `.utm`, o que significa que ele já vem configurado e compatível com o UTM.

1.  Vá até a pasta onde você baixou o arquivo do Parrot (geralmente um `.zip` ou arquivo comprimido).
2.  **Extraia** o arquivo. Você deverá ver um arquivo final com a extensão `.utm`.

## 3. Importando e Rodando
O processo de "instalação" é extremamente simples:

1.  Simplesmente **arraste e solte** o arquivo `.utm` extraído para dentro da janela do UTM.
2.  O sistema operacional será reconhecido imediatamente.
3.  Clique no ícone de **Play** (triângulo) para iniciar o Parrot no seu Mac.

> **Nota:** Se você baixou apenas a imagem **ISO** (ex: `Parrot-security-arm64.iso`) em vez do arquivo `.utm` pronto, você precisará clicar em "Create a New Virtual Machine" no UTM, selecionar "Virtualize" > "Linux" e selecionar a ISO manualmente.

---
**Pronto!** Agora você tem o Parrot rodando no seu Mac com Apple Silicon.
