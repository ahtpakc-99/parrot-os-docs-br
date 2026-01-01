# Instalação no VirtualBox

Este guia cobre passo a passo como criar uma Máquina Virtual (VM) para rodar o Parrot OS de forma segura dentro do seu sistema atual (seja Windows, macOS ou Linux).

## 1. Instalação do VirtualBox
Primeiro, você precisa ter o software de virtualização instalado.

* **Windows / macOS:** Baixe o instalador no [site oficial do VirtualBox](https://www.virtualbox.org/).
* **GNU/Linux (Debian/Ubuntu/Parrot):** Instale via terminal:
  ```bash
  sudo apt update && sudo apt install virtualbox virtualbox-ext-pack

## 2. Criando a Máquina Virtual
Abra o VirtualBox e clique no botão Novo (New).

Nome: Digite Parrot Security.

Imagem ISO: Selecione o arquivo .iso do Parrot que você baixou.

O VirtualBox deve detectar automaticamente o "Tipo" (Linux) e "Versão" (Debian 64-bit or Parrot).

Edição Unattended: Se aparecer uma tela de "Instalação Desassistida", clique em Pular (Skip Unattended Installation). Queremos instalar manualmente.

Hardware (RAM e CPU)
Memória Base (RAM): O mínimo é 512MB, mas recomendamos fortemente pelo menos 2048 MB (2 GB) ou mais para uma experiência fluida.

Processadores: Aloque pelo menos 2 CPUs.

EFI: Marque a caixa "Habilitar EFI" (Enable EFI).

Disco Rígido Virtual
Selecione "Criar um Novo Disco Rígido Virtual Agora".

Tamanho do Disco:

Para Home Edition: Mínimo 20 GB.

Para Security Edition: Mínimo 40 GB.

Alocação: Deixe marcada a opção "Pré-alocar tamanho total" se quiser performance máxima (ocupa todo o espaço do HD na hora), ou desmarque para crescer conforme o uso.

Clique em Finalizar.

## 3. Ajustes Finos (Importante)
Antes de ligar a máquina, vamos otimizar as configurações. Selecione sua VM do Parrot e clique em Configurações (Settings).

Geral > Avançado
Área de Transferência Compartilhada: Mude para Bidirecional.

Arrastar e Soltar: Mude para Bidirecional.

Isso permite copiar/colar texto e arquivos do seu Windows/Mac para dentro do Parrot e vice-versa.

Sistema > Placa-mãe
Ordem de Boot: Desmarque "Disquete" (Floppy).

Recursos Estendidos: Marque "Habilitar I/O APIC".

Sistema > Processador
Marque a caixa "Habilitar PAE/NX".

Monitor > Tela
Memória de Vídeo: Aumente para o máximo disponível (geralmente 128 MB).

Aceleração: Marque "Habilitar Aceleração 3D".

Isso deixa a interface gráfica muito mais rápida.

Rede
Certifique-se de que está conectado como NAT (padrão). Isso fará a VM usar a internet do seu computador.

Portas > USB
Para usar USB 2.0 ou 3.0, certifique-se de ter instalado o VirtualBox Extension Pack.

Selecione Controladora USB 3.0 (xHCI) para melhor velocidade.

Clique em OK para salvar tudo.

## 4. Instalação do Sistema
Agora está tudo pronto.

Na tela principal, clique em Iniciar (Start).

A VM vai abrir e carregar o Parrot. Selecione Try/Install e aperte Enter.

Quando o sistema carregar (Live Mode), clique duas vezes em Install Parrot.

O instalador Calamares vai abrir. Siga os passos padrões:

Idioma: Português do Brasil.

Teclado: Portuguese (Brazil) - Default.

Particionamento: Selecione Apagar disco (Erase Disk).

Nota: Como é uma máquina virtual, "Apagar disco" apagará apenas o disco virtual de 20/40GB que criamos, não o seu HD real. Pode ir sem medo.

Swap: Selecione "Swap to file" ou "No Swap".

Crie seu usuário e senha.

Clique em Instalar.

Após finalizar, reinicie a máquina virtual e aperte Enter quando pedir para remover a mídia de instalação.

Parabéns!
Você agora tem um Parrot OS completo rodando dentro do seu computador.
