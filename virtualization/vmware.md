# Instalação no VMware

É possível usar o Parrot OS no VMware em todas as suas edições (**Workstation Player**, **Workstation Pro**) e também no macOS (**Fusion Player** e **Fusion Pro**).

Este guia foca na criação de uma Máquina Virtual no **VMware Workstation Player** (que é gratuito para uso pessoal). Como as outras edições são extensões desta versão, o procedimento de configuração muda muito pouco.

## Passo 1 - Baixar e Instalar o VMware
Acesse o [site oficial da VMware](https://www.vmware.com/products/workstation-player.html) e baixe a versão para seu sistema operacional (Windows ou Linux).

### Instalação no Windows
Basta baixar o arquivo `.exe` e seguir o instalador padrão ("Next, Next, Finish").

### Instalação no Linux
Se você usa Linux, o arquivo baixado será um `.bundle`.
1. Abra o terminal na pasta onde baixou.
2. Dê permissão de execução:
   ```bash
   chmod +x ./VMware-Workstation-Full-xxxx.x86_64.bundle
Execute o instalador com sudo:

Bash

sudo ./VMware-Workstation-Full-xxxx.x86_64.bundle
O instalador gráfico abrirá. Siga as instruções e, ao final, o VMware estará no seu menu de aplicativos.

Passo 2 - Criar uma Nova Máquina Virtual
Abra o VMware.

Clique em Create a New Virtual Machine (Criar Nova Máquina Virtual).

Selecionando a ISO
Uma janela de assistente abrirá.

Selecione a opção Installer disc image file (iso).

Clique em Browse e selecione o arquivo ISO do Parrot que você baixou.

Clique em Next.

Nota: O VMware pode detectar incorretamente o sistema como "Debian 5" ou algo antigo. Não se preocupe, isso é normal e ajustaremos a seguir.

Escolhendo o Sistema Operacional
Se o VMware não detectar automaticamente:

Guest operating system: Selecione Linux.

Version: Selecione Debian 10.x 64-bit (ou a versão Debian mais recente disponível na lista, já que o Parrot é baseado no Debian Stable).

Nome e Local
Dê um nome para sua VM (Ex: Parrot Security).

Escolha onde ela será salva no seu computador.

Clique em Next.

Disco Rígido (Espaço)
Defina o tamanho do disco virtual. Consulte os requisitos da edição que você baixou:

Home Edition: Mínimo 20 GB.

Security Edition: Recomendado pelo menos 40 GB (devido às muitas ferramentas).

Selecione a opção "Split virtual disk into multiple files" (Dividir disco em vários arquivos) para facilitar a movimentação da VM depois, ou "Store as single file" para um leve ganho de performance.

Hardware (RAM e CPU)
A próxima tela mostrará um resumo. Clique no botão Customize Hardware para ajustar o desempenho:

Memory (RAM): Recomendamos pelo menos 4 GB (4096 MB) para uma experiência fluida.

Processors: Aloque pelo menos 2 cores.

Display/USB: Certifique-se de que a aceleração 3D e controladores USB estejam ativados.

Clique em Close e depois em Finish.

Passo 3 - Instalar o Parrot na VM
Sua Máquina Virtual está pronta, mas o disco ainda está "vazio".

Na lista lateral do VMware, selecione seu Parrot Security e clique em Play virtual machine.

A máquina irá ligar e carregar o menu do Parrot (GRUB).

Selecione Try / Install e aperte Enter.

A partir daqui, o processo é idêntico à instalação em um computador real. Siga o nosso Guia de Instalação Padrão.

Dica Pós-Instalação: Diferente do VirtualBox, o VMware costuma instalar as ferramentas de integração (VMware Tools / Open-VM-Tools) automaticamente durante a instalação do Parrot. Se a resolução de tela não se ajustar automaticamente após o primeiro reboot, abra o terminal e rode: sudo apt update && sudo apt install open-vm-tools-desktop E reinicie a VM.
