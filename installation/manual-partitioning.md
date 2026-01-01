# Particionamento Manual

O particionamento manual usando o instalador Calamares oferece controle total sobre como o ParrotOS será instalado.

Assim como no Dual Boot, este método permite atribuir tamanhos personalizados e determinar quantas partições criar ou editar.

Vamos abordar dois casos de uso comuns:
1.  **Caso 1:** Particionando um disco com partições existentes (Redimensionamento).
2.  **Caso 2:** Particionando um disco vazio (Instalação Limpa).

---

## Pré-requisitos (UEFI vs BIOS)
Antes de começar, desative o **Secure Boot** e o **CSM** nas configurações da UEFI da sua máquina.

### Para computadores UEFI (Modernos)
São necessárias pelo menos três partições:
* `/boot/efi`: Contém o firmware necessário para iniciar o sistema (Formato FAT32).
* `/`: A partição Raiz, onde o sistema é instalado.
* `/home`: A pasta de dados do usuário (Opcional, mas recomendado separar).

### Para computadores BIOS (Antigos)
São necessárias pelo menos duas partições:
* `/`: Raiz.
* `/home`: Dados do usuário.

---

## Caso 1: Disco com partições existentes
Use este método se você já tem outro sistema (como Windows) e quer instalar o Parrot ao lado, mas controlando os detalhes manualmente.

Ao selecionar **Particionamento Manual**, você verá seu disco atual (ex: `/dev/sda`).
* `/dev/sda1`: Geralmente é a partição de boot EFI.
* `/dev/sda2`: Geralmente é onde está o sistema operacional atual.

### Passo 1: Configurar o Boot (EFI)
1.  Selecione a partição EFI existente (`/dev/sda1` ou similar, formatada em FAT32).
2.  Clique em **Editar**.
3.  **Não formate!** Apenas defina o **Ponto de Montagem** (Mount Point) como `/boot/efi`.
4.  Clique em **OK**.

### Passo 2: Redimensionar o Sistema Atual
1.  Selecione a partição do sistema atual (ex: `/dev/sda2`).
2.  Clique em **Editar**.
3.  Arraste a barra ou digite o tamanho para diminuir essa partição e liberar espaço para o Parrot.
    * *Nota: Deixe pelo menos 20GB (Home Edition) ou 40GB (Security Edition) livres.*
4.  Clique em **OK**.

### Passo 3: Criar a Raiz (Root)
1.  Selecione o **Espaço Livre** (Free Space) que foi criado.
2.  Clique em **Criar**.
3.  Defina o tamanho (ex: 30GB).
4.  Defina o Ponto de Montagem como `/` (Raiz).
5.  Sistema de Arquivos: **Btrfs** (recomendado) ou Ext4.
6.  Clique em **OK**.

### Passo 4: Criar a Home
1.  Selecione o restante do Espaço Livre.
2.  Clique em **Criar**.
3.  Defina o Ponto de Montagem como `/home`.
4.  Sistema de Arquivos: **Btrfs** ou Ext4.
5.  Clique em **OK**.

Clique em **Próximo** para prosseguir com a instalação.

---

## Caso 2: Particionando um disco vazio
Use este método se o disco é novo ou se você quer apagar tudo e criar uma estrutura personalizada do zero.

Ao selecionar **Particionamento Manual**, o espaço aparecerá como "não alocado".

### Passo 1: Nova Tabela de Partição
1.  Clique no botão **Nova Tabela de Partição** (New Partition Table).
2.  Selecione **GPT** (padrão para sistemas modernos).
3.  Clique em **OK**.

### Passo 2: Criar a Partição EFI (/boot/efi)
1.  Selecione o "Espaço Livre" e clique em **Criar**.
2.  **Tamanho:** Defina `500 MiB` (ou mínimo de 200 MiB).
3.  **Sistema de Arquivos:** Selecione **fat32**.
4.  **Ponto de Montagem:** Selecione `/boot/efi`.
5.  Clique em **OK**.

### Passo 3: Criar a Raiz (/)
Esta é a pasta onde o sistema operacional ficará.
1.  Selecione o "Espaço Livre" restante e clique em **Criar**.
2.  **Tamanho:** Defina o tamanho desejado (Mínimo 20GB para Home, 40GB para Security).
3.  **Sistema de Arquivos:** Selecione **btrfs** (padrão moderno do Parrot) ou ext4.
4.  **Ponto de Montagem:** Selecione `/`.
5.  Clique em **OK**.

### Passo 4: Criar a Home (/home)
Opcional, mas útil para salvar seus arquivos se precisar formatar a Raiz no futuro.
1.  Selecione o "Espaço Livre" final e clique em **Criar**.
2.  **Tamanho:** Use todo o restante disponível.
3.  **Sistema de Arquivos:** **btrfs** ou ext4.
4.  **Ponto de Montagem:** Selecione `/home`.
5.  Clique em **OK**.

### Finalizando
Sua tabela deve mostrar as três partições configuradas corretamente. Clique em **Próximo** para iniciar a instalação.
