# Dual Boot com Windows

É possível instalar o ParrotOS ao lado do Windows, graças ao GRUB e um particionamento correto.

> **Nota Importante:**
> Antes de começar, desative o **Secure Boot** e o **CSM (Legacy Mode)** nas configurações da UEFI (BIOS) da sua máquina.

Depois de seguir os passos iniciais da [Instalação Padrão](install-guide.md) até chegar na etapa de particionamento, você verá o seu disco com o Windows já instalado.

Existem duas maneiras de prosseguir:
1.  **Método 1:** Particionamento Automatizado (Mais Fácil)
2.  **Método 2:** Particionamento Manual (Avançado)

---

## Método 1: Particionamento Automatizado
Esta é a maneira mais fácil. O instalador faz o trabalho difícil para você.

1.  Na tela de particionamento, selecione a opção **"Instalar lado a lado"** (*Install alongside*).
2.  Selecione a partição onde o Windows está instalado (geralmente `/dev/sda3` ou a maior partição NTFS).
3.  Uma barra deslizante aparecerá. **Arraste a barra inferior** para redimensionar a partição e definir quanto espaço você quer deixar para o Windows e quanto quer dar para o ParrotOS.
4.  Clique em **Próximo** e prossiga com a instalação.

---

## Método 2: Particionamento Manual
Este método oferece a liberdade de escolher a quantidade exata de espaço e criar partições personalizadas (como separar a `/home`).

> **Requisitos de Espaço:**
> * **Security Edition:** Precisa de pelo menos **40GB**.
> * **Home Edition:** Precisa de pelo menos **20GB**.
> * **Swap:** Se você usa SSD, geralmente não precisa de partição Swap dedicada (o sistema usa Swapfile).

1. Selecione **Particionamento Manual** e clique em **Próximo**.

Você verá a estrutura atual do seu disco. Em uma instalação padrão do Windows, geralmente temos:
* `/dev/sda1`: Partição de Boot (EFI).
* `/dev/sda2`: MSR (Reservado pela Microsoft).
* `/dev/sda3`: Onde o Windows (C:) está instalado.
* `/dev/sda4`: Partição de Recuperação do Windows.

### Passo A: Redimensionar o Windows
Precisamos "encolher" o Windows para abrir espaço.
1. Selecione a partição do Windows (ex: `/dev/sda3`) e clique em **Editar**.
2. Arraste a barra ou digite o novo tamanho em MiB para liberar espaço.
   * *Exemplo:* Se o disco tem 60GB, você pode deixar 40GB para o Windows e liberar 20GB para o Parrot.
3. Clique em **OK**.

### Passo B: Criar a Partição do Parrot
Agora você terá um espaço cinza chamado "Espaço livre" (Free space).
1. Selecione o espaço livre e clique em **Criar**.
2. Defina as configurações:
   * **Sistema de Arquivos:** Escolha `btrfs` (padrão do Parrot) ou `ext4`.
   * **Ponto de Montagem:** Selecione `/` (Raiz).
3. Clique em **OK**.

### Passo C: Configurar o Boot (EFI)
Este é o passo mais importante para que o Dual Boot funcione.
1. Encontre a partição de boot original do Windows (geralmente `/dev/sda1`, formatada em FAT32).
2. Selecione-a e clique em **Editar**.
3. **Não formate!** Apenas altere a opção **Ponto de Montagem**.
4. Selecione `/boot/efi` como ponto de montagem.
   * *Nota: Certifique-se de manter a flag `boot` marcada se houver opção.*
5. Clique em **OK**.

### Finalizando
O resumo das partições deve mostrar o Windows redimensionado, a nova partição do Parrot (`/`) e a partição de boot (`/boot/efi`) configurada.
Clique em **Próximo** para instalar.
