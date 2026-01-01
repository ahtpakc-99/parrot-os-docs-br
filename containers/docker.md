# Parrot no Docker

O Docker é uma tecnologia poderosa que permite aos usuários rodar containers universalmente em qualquer plataforma hospedeira.

O Docker utiliza imagens de modelo (templates) e permite ao usuário iniciar várias instâncias do mesmo modelo, destruí-las ou construir novos modelos personalizados sobre elas.

O Parrot usa o docker para permitir que seus usuários utilizem seu vasto arsenal de ferramentas em qualquer plataforma suportada pelo docker (Linux, Windows, macOS).

## Imagens Disponíveis (Templates)
Seja para ter um container cheio de ferramentas, vários containers menores com uma seleção específica, ou até mesmo um ambiente Parrot limpo para construir sua própria stack, este é o lugar certo para aprender a aproveitar o espaço de trabalho do Parrot Docker.

### 1. Parrot Core (`parrotsec/core`)
O sistema principal apenas com o básico do Parrot. Você pode usá-lo como ponto de partida para criar seus próprios containers personalizados.
* **Arquitetura:** Esta imagem é multi-arquitetura e funciona para amd64, arm64 e armhf.

**Iniciar o container:**

docker run --rm -ti --network host -v $PWD/work:/work parrotsec/core

### 2. Parrot Security (parrotsec/security)
Este container inclui uma enorme coleção de ferramentas que podem ser usadas via linha de comando de dentro de um container docker.

Nota: Algumas ferramentas com interface gráfica foram excluídas por razões óbvias.

Conteúdo: Este container vem com o metapackage parrot-cloud.

Iniciar o container:

docker run --rm -ti --network host -v $PWD/work:/work parrotsec/security
Ferramentas Individuais
Esta é uma seleção curada de containers docker menores que contêm apenas ferramentas específicas, sozinhas ou em coleções selecionadas. Containers com ferramentas compartilhadas são empilhados uns sobre os outros (quando possível) para minimizar o desperdício de armazenamento e maximizar a reutilização de camadas.

Nmap (parrotsec/nmap)
Baseado em parrotsec/core, fornece os seguintes pacotes: nmap, ncat, ndiff, dnsutils, netcat, telnet.

Uso:

docker run --rm -ti parrotsec/nmap <opções do nmap>
Exemplos:

# Scan rápido
docker run --rm -ti parrotsec/nmap -F 192.168.1.1

# Scan sem ping
docker run --rm -ti parrotsec/nmap -Pn 89.36.210.176
Metasploit (parrotsec/metasploit)
Baseado em parrotsec/nmap:latest, fornece os seguintes pacotes: nmap, metasploit-framework, postgresql.

Uso:

docker run --rm -ti --network host -v $PWD/msf:/root/ parrotsec/metasploit
Social Engineering Toolkit (parrotsec/set)
Baseado em parrotsec/metasploit:latest, fornece os seguintes pacotes: set.

Uso:

docker run --rm -ti --network host -v $PWD/set:/root/.set parrotsec/set
Beef-XSS (parrotsec/beef)
Baseado em parrotsec/core, fornece os seguintes pacotes: beef-xss.

Uso:

docker run --rm --network host -ti -v $PWD/beef:/var/lib/beef-xss parrotsec/beef
Bettercap (parrotsec/bettercap)
Baseado em parrotsec/nmap, fornece os seguintes pacotes: bettercap.

Uso:

docker run --rm -ti --network host parrotsec/bettercap
SQLMap (parrotsec/sqlmap)
Baseado em parrotsec/nmap, fornece os seguintes pacotes: sqlmap.

Uso:

docker run --rm -ti parrotsec/sqlmap <opções do sqlmap>
Exemplo:

docker run --rm -ti parrotsec/sqlmap -u parrotsec.org --wizard
