# Apple Container (macOS Silicon)

Durante a WWDC mais recente (2025), foi anunciada e lançada a **Containerização**, um software que "executa cada container Linux dentro de sua própria máquina virtual leve" em processadores **Apple Silicon**, começando a partir do **macOS 15 Sequoia** e **macOS 26 Tahoe**.

Através da Containerização, temos outra maneira de gerenciar imagens compatíveis com OCI (*Open Container Initiative*); como resultado, também podemos usar as imagens Docker do Parrot.

**Por que isso funciona?**
Porque as imagens Docker do Parrot são compatíveis com OCI (*OCI-compliant*), permitindo que sejam usadas nesta nova plataforma sem problemas.

## Instalação do `container`

O `container` é uma ferramenta de linha de comando (CLI) que permite usar as APIs de Containerização da Apple para criar e gerenciar essas imagens.

> **Requisito:** É recomendado atualizar o macOS para a versão estável mais recente.

Embora possa ser instalado diretamente da página de Releases do GitHub, a maneira mais fácil é usar o **Homebrew**:

```bash
brew install --cask container

```

### Comandos Básicos

Após instalar, você pode verificar a instalação digitando `container`:

```text
$ container
OVERVIEW: A container platform for macOS

USAGE: container [--debug] <subcommand>

OPTIONS:
  --debug                 Enable debug output [environment: CONTAINER_DEBUG]
  --version               Show the version.
  -h, --help              Show help information.

CONTAINER SUBCOMMANDS:
  create                  Create a new container
  delete, rm              Delete one or more containers
  exec                    Run a new command in a running container
  inspect                 Display information about one or more containers
  kill                    Kill one or more running containers
  list, ls                List containers
  logs                    Fetch container stdio or boot logs
  run                     Run a container
  start                   Start a container
  stop                    Stop one or more running containers

IMAGE SUBCOMMANDS:
  build                   Build an image from a Dockerfile
  images, image, i        Manage images
  registry, r             Manage registry configurations

SYSTEM SUBCOMMANDS:
  builder                 Manage an image builder instance
  system, s               Manage system components

```

### Iniciando o Serviço

Antes de rodar imagens, você deve iniciar o serviço do sistema:

```bash
container system start

```

Isso inicia o servidor de containers. Se um kernel padrão ainda não estiver instalado, ele será baixado e configurado automaticamente (o kernel padrão é fornecido pelo **Kata Containers**, uma solução de VM leve).

---

## Usando Containers ParrotOS no Apple Silicon

Os comandos são muito semelhantes ao Docker ou Podman (ex: `container list --all`, `build`, etc).

Como as imagens do Parrot são compatíveis, você pode iniciá-las diretamente.

**Para rodar o Parrot Core:**

```bash
container run --rm -it parrotsec/core

```

**Para rodar o Parrot Security:**

```bash
container run --rm -it parrotsec/security

```

### Visão Geral Técnica

Para mais detalhes sobre a arquitetura, consulte a documentação técnica oficial do `container`.
