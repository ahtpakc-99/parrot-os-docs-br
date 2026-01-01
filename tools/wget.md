# Wget

O **Wget** é uma ferramenta de linha de comando (CLI) que permite baixar arquivos e interagir com APIs REST de forma interativa. Ele oferece suporte aos protocolos HTTP, HTTPS, FTP e FTPS.

Abaixo estão os casos de uso mais comuns:

## 1. Download Direto de Arquivo
```bash
wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.39.2.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.39.2.tar.bz2)

```

Este é o comando básico. Ao executá-lo, o arquivo será baixado diretamente na pasta onde o terminal está aberto.

## 2. Download em Segundo Plano (`-b`)

```bash
wget -b [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.39.2.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.39.2.tar.bz2)

```

Esta opção é extremamente útil ao iniciar um download em uma máquina remota via SSH. O download será iniciado em segundo plano, permitindo que o usuário se desconecte do terminal sem interromper o processo.

## 3. Retomar Downloads Interrompidos (`-c`)

```bash
wget -c [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.39.2.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.39.2.tar.bz2)

```

Um comando indispensável para baixar arquivos grandes que podem ser interrompidos. Se um arquivo com o mesmo nome já existir, o Wget verificará seu tamanho e baixará apenas a parte restante, em vez de começar do zero.

## 4. Número Máximo de Tentativas (`--tries`)

```bash
wget --tries=10 [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.39.2.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.39.2.tar.bz2)

```

Caso encontre um servidor lento ou congestionado, você pode definir um limite de tentativas para evitar que o comando fique tentando indefinidamente. No exemplo acima, o limite foi definido para 10.

## 5. Downloads Múltiplos (`-i`)

```bash
wget -i lista_downloads.txt

```

Esta opção permite fornecer um arquivo de texto contendo uma série de URLs. O Wget baixará sequencialmente todos os recursos listados no arquivo.

## 6. Limitar Velocidade de Download (`--limit-rate`)

```bash
wget --limit-rate=1k [http://www.kernel.org/pub/linux/kernel/v3.0/testing/patch-3.0-rc4.bz2](http://www.kernel.org/pub/linux/kernel/v3.0/testing/patch-3.0-rc4.bz2)

```

Se você precisar poupar largura de banda, o Wget permite limitar a velocidade. No exemplo acima, o limite foi definido para 1 kB/s.

---

## 7. Download com Proxy Ativado

Para baixar através de um proxy, não é necessário um comando especial do Wget, mas sim configurar uma variável de ambiente chamada `http_proxy`.

**Configuração básica:**

```bash
export http_proxy="http://meu-servidor-proxy:8080"

```

**Se o proxy exigir autenticação (usuário e senha):**

```bash
export http_proxy="http://usuario:senha@meu-servidor-proxy:8080"

```

Após exportar a variável, qualquer comando `wget` executado na mesma sessão de terminal passará automaticamente pelo proxy configurado.
