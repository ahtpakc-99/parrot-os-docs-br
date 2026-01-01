# Crie o seu Próprio Espelho

Você pode configurar um espelho do arquivo Parrot em seu servidor para uso pessoal ou público seguindo as etapas abaixo.

### Verifique o espaço livre

Você pode sincronizar o repositório inteiro ou apenas as imagens ISO. Certifique-se de ter espaço suficiente, pois o tamanho do arquivo flutua com o tempo.

* Consulte o tamanho atual aqui: [archive-size.txt](https://www.google.com/search?q=https://archive.parrotsec.org/parrot/misc/archive-size.txt)

---

## 1. Configuração via Docker (Recomendado)

Fornecemos uma imagem Docker pronta para facilitar o processo.

**Docker Compose (`docker-compose.yml`):**

```yaml
services:
  parrot-mirror:
    image: registry.gitlab.com/parrotsec/project/parrot-mirror-docker:main
    ports:
      - "8000:80" # Porta HTTP exposta
      - "873:873" # Porta do Daemon Rsync
    volumes:
      - ./mirror-tmp:/mirror # Local onde os arquivos serão armazenados
    environment:
      SOURCE: "rsync://rsync.parrot.sh:/parrot" # Fonte de sincronização
      BWLIMIT: "0" # Limite de largura de banda (0 = ilimitado)

```

> **Nota:** O volume deve ser montado internamente em `/mirror`.

---

## 2. Configuração Manual

### Escolha o servidor de origem (Upstream)

Recomendamos o uso do **rsync.parrot.sh** para configurações automáticas e à prova de falhas.

* **Diretor Principal:** `rsync.parrot.sh`
* **Zonas Globais:**
* Europa/Oriente Médio/África: `emea.rsync.parrot.sh`
* Américas: `ncsa.rsync.parrot.sh`
* Ásia/Pacífico: `apac.rsync.parrot.sh`



### Sincronizar o repositório completo

Se você sincronizar o arquivo completo, as imagens ISO já estarão incluídas por padrão.

1. **Sincronização manual:**
```bash
rsync -Pahv --delete-after rsync://rsync.parrot.sh:/parrot /var/www/html/parrot

```


2. **Configurar tarefa agendada (Cron):**
Digite `crontab -e` e adicione a linha abaixo para atualizar diariamente às 04:00:
```bash
0 4 * * * flock -xn /tmp/parrot-rsync.lock -c 'rsync -aq --delete-after rsync://rsync.parrot.sh:/parrot /var/www/html/parrot'

```



### Sincronizar apenas as imagens ISO

Use estas instruções apenas se **não** quiser o repositório completo de pacotes.

1. **Sincronização manual:**
```bash
rsync -Pahv --delete-after rsync://rsync.parrot.sh:/parrot-iso /var/www/html/parrot

```


2. **Configurar tarefa agendada (Cron):**
Adicione ao seu crontab para atualizar às 02:30:
```bash
30 2 * * * flock -xn /tmp/parrot-rsync.lock -c 'rsync -aq --delete-after rsync://rsync.parrot.sh:/parrot-iso /var/www/html/parrot'

```



---

## 3. Exponha seu Espelho via Rsync

Para que seu espelho seja oficial, ele **deve** ser exposto via protocolo rsync. Isso permite que nosso diretor de espelhos realize verificações de integridade.

1. **Instale o rsync:**
```bash
sudo apt install rsync

```

2. **Edite o arquivo `/etc/rsyncd.conf`:**
```bash
sudo nano /etc/rsyncd.conf

```

Cole as seguintes configurações:
```text
[parrot]
        comment = Parrot OS - full archive [rsync.parrot.sh/parrot]
        path = /var/www/html/parrot/
        hosts allow = *
        list=true
        uid=www-data
        gid=www-data
        read only = yes
        use chroot=yes
        dont compress

[parrot-iso]
        comment = Parrot OS - ISO files only [rsync.parrot.sh/parrot-iso]
        path = /var/www/html/parrot/
        exclude = pool dists
        hosts allow = *
        list=true
        uid=www-data
        gid=www-data
        read only = yes
        use chroot=yes
        dont compress

```

3. **Habilite e inicie o serviço:**
```bash
sudo systemctl enable rsync
sudo service rsync start

```

## 4. Torne seu espelho oficial

Se você deseja que seu servidor seja adicionado à lista oficial de espelhos do Parrot OS, envie um e-mail para **team@parrotsec.org**.
