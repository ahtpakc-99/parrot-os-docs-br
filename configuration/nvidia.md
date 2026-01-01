# Configuração de Drivers NVIDIA

Inicialmente, o Parrot usa os drivers de código aberto **Nouveau**, pois eles suportam a maioria das placas Nvidia. Eles garantem boa estabilidade e permitem usar a GPU sem problemas para tarefas diárias.

No entanto, pode ser necessário usar outros drivers para obter maior compatibilidade com softwares específicos (como quebra de senhas ou jogos) e aproveitar ao máximo sua GPU. Por esse motivo, você pode instalar os drivers oficiais da Nvidia (código fechado).

> **Atenção:** A instalação e configuração do driver podem ser diferentes para **Desktops** e **Laptops**.
> * Laptops geralmente possuem uma **iGPU** (integrada, Intel/AMD) e uma **dGPU** (dedicada, Nvidia).
> * As diferenças serão destacadas neste documento. Leia tudo com atenção.

---

## 1. Identificando sua GPU
Se você não sabe qual é o modelo da sua placa, abra o terminal e digite:

```bash
lspci | grep VGA

```

Para informações mais detalhadas sobre o driver em uso:

```bash
inxi -F

```

---

## 2. Instalação via Repositório (Método Padrão)

Se você confirmou que está usando o driver *nouveau* e quer mudar para o proprietário, siga estes passos.

### Passo 1: Bloquear (Blacklist) o Nouveau

Para evitar conflitos, devemos desativar o driver open source.

1. Abra/Crie o arquivo de configuração:
```bash
sudo nano /etc/modprobe.d/blacklist-nouveau.conf

```


2. Adicione as seguintes linhas e salve o arquivo (`Ctrl+O`, `Enter`, `Ctrl+X`):
```ini
blacklist nouveau
options nouveau modeset=0
alias nouveau off

```



### Passo 2: Instalar o Driver

Execute o comando de instalação:

```bash
sudo apt update && sudo apt install nvidia-driver

```

> **Nota para Kernels Recentes (5.16+):**
> Se houver problemas de compatibilidade, pode ser necessário instalar a versão backports:
> `sudo apt install nvidia-driver -t lory-backports`

### Passo 3: Verificação

Recomendamos instalar o utilitário oficial para verificar se tudo deu certo:

```bash
sudo apt install nvidia-smi

```

Execute `nvidia-smi` para ver o status da placa. Além disso, o **Nvidia Settings** será instalado automaticamente para gerenciar resolução e taxa de atualização.

---

## 3. Laptops com Placa Híbrida (iGPU + dGPU)

A maioria dos laptops modernos vem com uma placa integrada (Intel/AMD) e uma dedicada (Nvidia). Vamos configurar o **Bumblebee** para alternar entre elas.

### Passo 1: Instalar Pacotes e CUDA

```bash
sudo apt update
sudo apt install bumblebee-nvidia primus-nvidia primus-vk-nvidia nvidia-smi nvidia-cuda-dev nvidia-cuda-toolkit

```

*Se aparecer um aviso sobre conflito com o driver nouveau, clique em OK.*

### Passo 2: Bloquear o Nouveau

(Se você já fez isso no método anterior, pule para o passo 3).
Edite o arquivo `/etc/modprobe.d/blacklist-nouveau.conf` e adicione:

```ini
blacklist nouveau
options nouveau modeset=0
alias nouveau off

```

**Reinicie o computador.**

### Passo 3: Configurar o Bumblebee

Precisamos dizer ao Bumblebee qual driver usar.

1. Edite a configuração:
```bash
sudo nano /etc/bumblebee/bumblebee.conf

```


2. Procure a linha `Driver=` e mude para:
`Driver=nvidia`
3. Procure a linha `KernelDriver=` e mude para:
`KernelDriver=nvidia-current`
4. Salve e **Reinicie o computador**.

### Passo 4: Testando

Abra um terminal para monitorar a placa:

```bash
watch nvidia-smi

```

Em outro terminal, execute um programa usando a placa dedicada (exemplo com hashcat):

```bash
optirun hashcat -b -d 1

```

*No primeiro terminal, você deve ver o processo do hashcat aparecendo na lista da GPU.*

> **Dica:**
> * `primusrun`: Usa tecnologia PRIMUS.
> * `optirun`: Usa VirtualGL.
> 
> 

---

## 4. Instalação via Site Oficial da Nvidia (Avançado)

Use este método apenas se precisar de uma versão muito específica ou "Bleeding Edge" que não está no repositório.

### Passo 1: Download

Baixe o driver `.run` (Linux 64-bit) do [site oficial da Nvidia](https://www.nvidia.com/Download/index.aspx).

### Passo 2: Desativar Interface Gráfica

Para evitar conflitos com o servidor X, devemos instalar sem interface (Runlevel 3).

```bash
sudo systemctl set-default multi-user.target

```

### Passo 3: Preparação

1. **Bloqueie o Nouveau** (conforme explicado nos métodos anteriores no arquivo `blacklist-nouveau.conf`).
2. **Atualize o Initramfs** (Essencial):
```bash
sudo update-initramfs -u

```


3. **Reinicie a máquina:**
```bash
reboot

```



### Passo 4: Instalação

Ao reiniciar, você estará em uma tela preta de terminal (TTY). Logue com seu usuário.

1. Vá até a pasta do download.
2. Dê permissão de execução:
```bash
sudo chmod +x NVIDIA-Linux-x86_64-<versão>.run

```


3. Execute o instalador:
```bash
sudo ./NVIDIA-Linux-x86_64-<versão>.run

```


4. Siga o assistente de instalação.

### Passo 5: Reativar Interface Gráfica

Após terminar, restaure o modo gráfico:

```bash
sudo systemctl set-default graphical.target

```

Reinicie o computador e verifique com `nvidia-smi`.
