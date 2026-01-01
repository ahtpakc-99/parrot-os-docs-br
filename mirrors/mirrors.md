# Espelhos (Mirrors) do Parrot OS

O Projeto Parrot não entrega apenas um sistema pronto no formato ISO, mas também fornece uma vasta quantidade de software adicional que pode ser instalado separadamente através do repositório oficial.

O repositório do Parrot é usado para fornecer software oficialmente suportado, atualizações de sistema e correções de segurança.

## A Rede de Espelhos (Mirrors)
O software no arquivo do Parrot é entregue na forma de pacotes `.deb`. Esses pacotes são servidos por uma rede mundial de servidores espelhos que distribuem o mesmo conjunto de arquivos para garantir downloads mais rápidos.

O sistema Parrot vem configurado para usar os **Diretores do Arquivo Parrot**. Estes são servidores especiais que coletam todas as requisições dos usuários e as redirecionam automaticamente para o servidor de download geograficamente mais próximo disponível.

### Medidas de Segurança
A Rede de Espelhos do Parrot é protegida por **assinaturas digitais centralizadas**, o que impede que espelhos mal-intencionados injetem atualizações falsas.

Se um servidor tentar injetar um pacote falso, o sistema APT (gerenciador de pacotes) recusará automaticamente o download e exibirá um alerta. Isso garante uma cadeia de confiança direta entre os desenvolvedores e o usuário final, pois as assinaturas são aplicadas offline pelos mantenedores do Parrot, e não pelos servidores espelhos.

---

## Configuração e Ajustes Personalizados

O gerenciador de pacotes APT utiliza o arquivo `/etc/apt/sources.list` e qualquer arquivo `.list` encontrado no diretório `/etc/apt/sources.list.d/`.

> **Nota:** No Parrot, o arquivo `/etc/apt/sources.list` geralmente está vazio. A configuração padrão fica em: `/etc/apt/sources.list.d/parrot.list`.

### Conteúdo Padrão do `parrot.list`:
```bash
deb [https://deb.parrot.sh/parrot](https://deb.parrot.sh/parrot) lory main contrib non-free non-free-firmware
deb [https://deb.parrot.sh/parrot](https://deb.parrot.sh/parrot) lory-security main contrib non-free non-free-firmware
deb [https://deb.parrot.sh/parrot](https://deb.parrot.sh/parrot) lory-backports main contrib non-free non-free-firmware
#deb-src [https://deb.parrot.sh/parrot](https://deb.parrot.sh/parrot) lory main contrib non-free non-free-firmware

```

### Repositório de Testes (Updates)

O repositório `lory-updates` fornece atualizações antes de chegarem ao repositório principal. Ele é destinado a desenvolvedores e testadores beta. **Sugerimos não ativá-lo**, pois pode introduzir bugs não testados e tornar o sistema instável.

---

## Espelhos para Configuração Manual

Se você preferir configurar manualmente um servidor específico para obter melhores velocidades em sua região, aqui estão as opções mais relevantes:

### 🌍 Mundiais (CDN)

| ID do Espelho | Provedor | URL |
| --- | --- | --- |
| **parrot** | Infraestrutura Parrot | `deb.parrot.sh/parrot` |
| **bunny** | Bunny.net | `bunny.deb.parrot.sh` |
| **alibaba** | Alibaba Cloud | `mirrors.aliyun.com/parrot` |

### 🇧🇷 Américas (Destaque para o Brasil)

| Localização | Provedor | Configuração APT (String) |
| --- | --- | --- |
| **Brasil (São Paulo)** | **USP** | `deb http://sft.if.usp.br/parrot/ lory main contrib non-free non-free-firmware` |
| **Equador** | CEDIA | `deb https://mirror.cedia.org.ec/parrot/ lory main contrib non-free non-free-firmware` |
| **EUA (MIT)** | SIPB MIT | `deb http://mirrors.mit.edu/parrot/ lory main contrib non-free non-free-firmware` |
| **EUA (Princeton)** | Princeton Univ. | `deb https://mirror.math.princeton.edu/pub/parrot/ lory main contrib non-free non-free-firmware` |

### 🇪🇺 Europa e Outros (Principais)

| Localização | Provedor | Largura de Banda |
| --- | --- | --- |
| **Itália** | GARR | 100 Gbps |
| **Alemanha** | RWTH-Aachen | 20 Gbps |
| **Suécia** | ACC Umeå | 200 Gbps |
| **Rússia** | Yandex | 1 Gbps |
| **Taiwan** | NCHC | 20 Gbps |

---

**Como mudar o espelho:**

1. Edite o arquivo: `sudo nano /etc/apt/sources.list.d/parrot.list`
2. Substitua o endereço `https://deb.parrot.sh/parrot` pelo link do espelho escolhido (ex: `http://sft.if.usp.br/parrot/`).
3. Salve e execute `sudo apt update`.
