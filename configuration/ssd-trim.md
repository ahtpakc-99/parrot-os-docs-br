# SSD TRIM (Otimização de Disco)

O **SSD TRIM** permite que a unidade verifique e exclua blocos de dados que não são mais necessários. Isso significa que o disco estará sempre pronto para gravar novos dados quando os antigos forem excluídos, garantindo que os blocos não fiquem ocupados desnecessariamente e melhorando a performance e vida útil do SSD.

Para configurar o SSD TRIM, abra o terminal e siga os passos abaixo:

## 1. Verificação de Suporte
Primeiro, identifique sua unidade e verifique se ela suporta a tecnologia TRIM.

```bash
sudo fdisk -l
sudo hdparm -I /dev/sdx

```

*(Substitua `/dev/sdx` pelo identificador do seu disco SSD, por exemplo: `/dev/sda`)*.

> **Nota:** Se o recurso for suportado, a saída do comando deverá conter a seguinte linha:
> `Data Set Management TRIM supported`

## 2. Backup do Fstab

Antes de editar arquivos críticos do sistema, é recomendável fazer um backup.

```bash
sudo cp /etc/fstab /opt/fstab.bak

```

## 3. Editando o Fstab

Abra o arquivo de configuração de montagem com o editor de texto:

```bash
sudo pluma /etc/fstab

```

O arquivo conterá linhas parecidas com esta:

> *Nota: Os UUIDs listados abaixo são apenas exemplos, o seu será diferente.*

`UUID=1cd2fc4f-7d99-4c7a-8ea7-6f9a2d5e5960 /   ext4 errors=remount-ro 0`

### A Alteração

Você deve adicionar a opção `discard,` imediatamente antes de `errors=remount-ro`.

**O resultado final da linha deve ficar assim:**

```text
UUID=1cd2fc4f-7d99-4c7a-8ea7-6f9a2d5e5960 /   ext4 discard,errors=remount-ro 0

```

Salve o arquivo e reinicie o computador para aplicar as mudanças.
