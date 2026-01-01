```markdown
# Usos e Exemplos do Docker

## Ciclo de Vida Básico

**Iniciar um container**
```bash
docker run --name pcore-1 -ti parrotsec/core
```

> **Nota:** O nome `pcore-1` é arbitrário e pode ser personalizado conforme sua preferência.

**Parar o container**

```bash
docker stop pcore-1

```

**Retomar um container parado anteriormente**

```bash
docker start pcore-1

```

**Remover um container após o uso**

```bash
docker rm pcore-1

```

**Listar todos os containers instanciados**

```bash
docker ps -a

```

---

## Múltiplos Containers

Você pode rodar várias instâncias simultaneamente em terminais diferentes.

**No terminal 1:**

```bash
docker run --name pentest1 -ti parrotsec/security

```

**No terminal 2:**

```bash
docker run --name pentest2 -ti parrotsec/security

```

**No terminal 3:**

```bash
docker run --name msf-listener -ti parrotsec/metasploit

```

### Limpeza em Massa

**Remover todos os containers de uma vez**

```bash
docker rm $(docker ps -qa)

```

**Iniciar um container e removê-lo automaticamente ao sair**
Use a flag `--rm` para que o container se autodestrua ao ser fechado, economizando espaço.

```bash
docker run --rm -ti parrotsec/core

```

---

## Persistência de Dados (Volumes)

### Compartilhar arquivos com o Host

É uma boa prática não manter containers persistentes, mas sim removê-los a cada uso, garantindo que arquivos importantes sejam salvos em um **Volume Docker**.

O comando a seguir cria uma pasta `work` dentro do diretório atual do seu computador e a monta em `/work` dentro do container.

```bash
docker run --rm -ti -v $PWD/work:/work parrotsec/core

```

### Compartilhar arquivos entre múltiplos containers

Você pode montar o mesmo volume em vários containers para que eles compartilhem os mesmos dados.

**No terminal 1:**

```bash
docker run --name pentest -ti -v $PWD/work:/work parrotsec/security

```

**No terminal 2:**

```bash
docker run --rm --network host -v $PWD/work:/work -ti parrotsec/security

```

**No terminal 3:**

```bash
docker run --rm -v $PWD/work:/work -ti parrotsec/metasploit

```

---

## Redes e Portas

### Abrir uma porta do container para o Host

Cada container Docker tem seu próprio espaço de rede conectado a uma LAN virtual. Todo o tráfego de dentro do container passará por NAT pelo computador host.

Se você precisa expor uma porta para outras máquinas fora do seu computador local (ex: rodar um servidor web no container e acessar pelo navegador do Windows), use a flag `-p`:

```bash
docker run --rm -p 8080:80 -ti parrotsec/core

```

> **Nota:** A primeira porta (`8080`) é a que será aberta no seu **Host**, e a segunda (`80`) é a porta do **Container** que será vinculada.

**Referência de uso da flag `-p`:**

* `-p <porta host>:<porta container>` (ex: `-p 8080:80`)
* `-p <porta host>:<porta container>/<protocolo>` (ex: `-p 8080:80/tcp`)
* Caso tenha múltiplos IPs no host: `-p <endereço>:<porta host>:<porta container>` (ex: `-p 192.168.1.30:8080:80`)

### Usar Rede "Host" (Host Networking)

Se você precisa que o container compartilhe **exatamente o mesmo espaço de rede** da máquina host (sem NAT), use a flag `--network host`.

```bash
docker run --rm --network host -ti parrotsec/core

```

> **⚠️ Avisos Importantes:**
> * Todas as portas abertas no container serão abertas automaticamente no host também.
> * Você poderá realizar sniffing de pacotes (captura de tráfego) da rede do host.
> * Regras de `iptables` aplicadas dentro do container terão efeito no host também.
> 
> 

```

```
