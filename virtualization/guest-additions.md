# VirtualBox Guest Additions

Os **Guest Additions** (Adicionais para Convidado) são drivers e aplicativos de sistema projetados para serem instalados dentro da máquina virtual após a instalação do sistema operacional.

Eles otimizam o sistema convidado (Parrot) para melhor desempenho e usabilidade.

## Principais Recursos
* **Integração do mouse:** Você não precisa mais apertar a tecla "Host" (geralmente Ctrl Direito) para libertar o mouse da janela da VM.
* **Pastas Compartilhadas:** Permite trocar arquivos facilmente entre seu computador real (Host) e o Parrot.
* **Melhor suporte de vídeo:** Permite resoluções de tela altas (Full HD/4K), redimensionamento automático da janela e aceleração de vídeo.
* **Janelas Seamless:** Permite que janelas do Parrot apareçam na área de trabalho do seu Windows como se fossem nativas.
* **Sincronização de horário:** Mantém a hora do Parrot sincronizada com o Host.
* **Área de transferência compartilhada:** Copie texto no Windows e cole no Parrot (e vice-versa).

---

## Como Instalar

Existem dois métodos. Recomendamos fortemente o **Método 1**, pois é mais limpo e fácil de atualizar.

### Método 1: Via Repositório (Recomendado)
Este método usa os pacotes oficiais do Parrot, garantindo maior compatibilidade.

1.  Abra um terminal no Parrot.
2.  Atualize a lista de pacotes:
    ```bash
    sudo apt update
    ```
3.  Instale os utilitários do VirtualBox:
    ```bash
    sudo apt install virtualbox-guest-utils virtualbox-guest-x11
    ```
4.  Quando a instalação terminar, reinicie a máquina virtual:
    ```bash
    sudo reboot
    ```
5.  Após reiniciar, verifique se tudo está rodando corretamente com o comando:
    ```bash
    sudo /usr/sbin/VBoxService -V
    ```
    *(Se aparecer a versão do VirtualBox, sucesso! Tente redimensionar a janela para testar).*

---

### Método 2: Via Imagem ISO (Alternativo)
Use este método apenas se o anterior falhar. Ele envolve "inserir" um CD virtual com os drivers.

1.  Na barra de menu da janela do VirtualBox, selecione **Dispositivos** > **Inserir imagem de CD dos Adicionais para Convidado...** (*Insert Guest Additions CD image*).
    * *Nota: Se o VirtualBox pedir para baixar a imagem, clique em **Baixar** e depois em **Inserir**.*
    * *Se der erro de montagem, desligue a VM, vá em Configurações > Armazenamento e adicione um segundo drive de CD vazio.*

2.  O CD aparecerá montado no Parrot (provavelmente na área de trabalho ou gerenciador de arquivos).
3.  Abra a pasta do CD, clique com o botão direito em uma área vazia e escolha **"Abrir Terminal Aqui"**.
4.  Dê permissão de execução ao instalador:
    ```bash
    sudo chmod +x VBoxLinuxAdditions.run
    ```
5.  Execute o instalador:
    ```bash
    sudo ./VBoxLinuxAdditions.run
    ```
6.  Aguarde o término da instalação e reinicie a máquina virtual:
    ```bash
    sudo reboot
    ```
