# Rclone

O **rclone** é uma ferramenta de linha de comando (CLI) que facilita o gerenciamento e a sincronização de arquivos e diretórios em armazenamentos na nuvem e sistemas remotos. Ele possui suporte oficial para Google Drive, Dropbox, Amazon S3 e muitos outros serviços.

### Casos de uso comuns do rclone:
* **Montagem de Remotos:** Monte um sistema de armazenamento remoto como se fosse um sistema de arquivos local usando `rclone mount`.
* **Filtros e Exclusões:** Use filtros para incluir ou excluir arquivos com base em padrões (regex).
* **Limite de largura de banda:** Limite a taxa de transferência para evitar o uso excessivo da sua rede.
* **Criptografia e Cache:** Use o backend `crypt` para criptografar arquivos e o backend `cache` para acesso mais rápido.
* **Backups Agendados:** Agende comandos do rclone usando `cron jobs` ou outros mecanismos de agendamento.

---

## 1. Instalação e Configuração

Primeiro, abra uma janela de terminal e instale o pacote:

```bash
sudo apt update && sudo apt install rclone

```

Após a instalação, é necessário configurá-lo para se conectar aos seus serviços de nuvem:

```bash
rclone config

```

O assistente de configuração solicitará o **nome do remoto**, o **tipo de armazenamento** e as **credenciais** (chaves de API, tokens de autenticação, etc.). Certifique-se de seguir as instruções fornecidas pelo seu provedor de nuvem e ter essas credenciais em mãos.

---

## 2. Uso Básico

> **Dica de Segurança:** É uma excelente prática testar qualquer comando de cópia ou sincronização adicionando a flag `--dry-run` ao final. Após garantir que a simulação está correta, repita o comando sem essa opção.

**Listar todos os remotos configurados:**

```bash
rclone listremotes

```

**Copiar arquivos da origem para o destino:**

```bash
rclone copy origem:caminho destino:caminho

```

*Onde `origem:caminho` pode ser uma pasta local ou remota, e `destino:caminho` é o local de recebimento.*

**Sincronizar armazenamentos:**

> **Atenção:** O comando `sync` altera apenas o destino. Ele faz com que o destino fique idêntico à origem, deletando arquivos no destino que não existem na origem.

```bash
rclone sync origem:caminho destino:caminho

```

**Listar todos os arquivos em um remoto:**

```bash
rclone ls remoto:caminho

```

**Deletar arquivos de um caminho específico no remoto:**

```bash
rclone delete remoto:caminho

```
