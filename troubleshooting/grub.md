# Recuperação do GRUB

Este guia apresenta soluções conhecidas para quando você estiver enfrentando problemas com o GRUB (o gerenciador de inicialização).

> **Para saber mais sobre o GRUB:**
> * [GRUB - gnu.org](https://www.gnu.org/software/grub/)
> * [GRUB - Wikipedia](https://en.wikipedia.org/wiki/GNU_GRUB)

---

## Passo 1 - Iniciar com ParrotOS Live USB
Para reparar o GRUB, você não pode estar dentro do sistema quebrado.
1.  Baixe a última ISO do ParrotOS.
2.  Grave-a em um pendrive (usando Etcher ou Rufus).
3.  Dê boot no computador usando este pendrive (Modo Live).

## Passo 2 - Identificação de Disco e Partição
Uma vez no modo Live, abra o terminal e digite:

```bash
sudo fdisk -l

```

A saída mostrará seus discos.

* **`/dev/sda`**: Geralmente é o primeiro SSD ou HDD (SATA).
* **`/dev/nvme0n1`**: Se você tem um SSD M.2 moderno, o nome será este.

Identifique as partições:

* **`/dev/sda1`** (exemplo): Geralmente é a partição **EFI** (sistema de arquivos FAT32), usada para boot em sistemas UEFI.
* **`/dev/sda2`** (exemplo): É a partição onde o **ParrotOS** (sistema de arquivos Btrfs) está instalado.

## Passo 3 - Criar pastas de montagem

Precisamos de pastas temporárias para montar seu sistema original. No terminal:

```bash
sudo mkdir /mnt
sudo mkdir -p /mnt/boot/efi

```

*Isso cria a estrutura necessária para montar a partição raiz e a partição EFI.*

## Passo 4 - Montar as Partições

Agora vamos montar as partições do seu disco rígido no sistema Live.

1. **Montar a Raiz (Root):**
Como o sistema de arquivos padrão do Parrot é **Btrfs** e usa subvolumes, o comando requer o argumento `subvol=@`:
```bash
sudo mount -o subvol=@ /dev/sda2 /mnt

```


*(Substitua `/dev/sda2` pela sua partição do Parrot).*
2. **Montar diretórios de sistema (Binding):**
Necessário para que o chroot funcione e tenha acesso ao hardware:
```bash
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

```


3. **Montar a partição EFI:**
```bash
sudo mount /dev/sda1 /mnt/boot/efi

```


*(Substitua `/dev/sda1` pela sua partição EFI).*

## Passo 5 - Acessar via Chroot e Instalar GRUB

Agora vamos "entrar" no seu sistema instalado.

1. Entre no ambiente chroot:
```bash
sudo chroot /mnt

```


2. Reinstale o GRUB no disco principal:
```bash
grub-install /dev/sda

```


*(Note que aqui usamos o disco `/dev/sda`, e não a partição `sda1`)*.
3. Atualize a configuração do GRUB (opcional, mas recomendado):
```bash
update-grub

```


4. Saia do ambiente chroot:
```bash
exit

```



## Passo 6 - Desmontar e Reiniciar

Agora que o reparo foi feito, vamos desmontar tudo com segurança.

```bash
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/boot/efi
sudo umount /mnt

```

Agora, reinicie o computador:

```bash
reboot

```

Remova o pendrive. Você deve ter um GRUB restaurado e funcionando perfeitamente.
