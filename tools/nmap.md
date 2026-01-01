# Nmap (Network Mapper)

O **Nmap** (Network Mapper) é uma ferramenta utilitária gratuita e de código aberto para descoberta de rede e auditoria de segurança. Administradores de sistemas e de rede também a consideram útil para tarefas como inventário de rede, gerenciamento de cronogramas de atualização de serviços e monitoramento de uptime de hosts ou serviços.

O Nmap utiliza pacotes IP brutos (raw) de formas inovadoras para determinar quais hosts estão disponíveis na rede, quais serviços (nome do aplicativo e versão) esses hosts estão oferecendo, quais sistemas operacionais (e versões de OS) eles estão executando, que tipo de filtros de pacotes/firewalls estão em uso e dezenas de outras características.

### Vantagens do Nmap:
* **Flexível:** Suporta dezenas de técnicas avançadas.
* **Poderoso:** Capaz de varrer redes imensas com milhares de máquinas.
* **Portátil:** Funciona em Linux, Windows e macOS.
* **Bem documentado:** Possui manuais extensos e suporte da comunidade.

**Exemplo de comando padrão:**
```bash
nmap -A -T4 scanme.nmap.org

```

---

## Descoberta de Hosts (Host Discovery)

O primeiro passo de qualquer missão de reconhecimento é reduzir um conjunto de faixas de IP em uma lista de hosts ativos. Escanear cada porta de cada endereço IP é lento e desnecessário.

### Comandos de Descoberta:

* **`-sL` (List Scan):** Apenas lista os alvos, sem enviar pacotes aos hosts.
* **`-sn` (No port scan):** Desativa o escaneamento de portas. Faz apenas a descoberta de hosts (antigo `-sP`).
* **`-Pn` (No ping):** Pula a descoberta de hosts. Trata todos os IPs como ativos (útil para firewalls que bloqueiam ICMP).
* **`-PS <lista de portas>`:** Ping TCP SYN para portas específicas.
* **`-PA <lista de portas>`:** Ping TCP ACK para portas específicas.
* **`-PU <lista de portas>`:** Ping UDP.
* **`-PE; -PP; -PM`:** Tipos de Ping ICMP (Echo, Timestamp e Address Mask).
* **`--traceroute`:** Rastreia o caminho do salto até o host.
* **`-n`:** Não faz resolução DNS (mais rápido).
* **`-R`:** Força resolução DNS para todos os alvos.

---

## Fundamentos do Escaneamento de Portas

Embora o Nmap tenha crescido em funcionalidade, ele começou como um scanner de portas eficiente. O comando simples `nmap <alvo>` escaneará as 1.000 portas TCP mais comuns.

### Os Seis Estados de Porta reconhecidos pelo Nmap:

1. **open (aberta):** Um aplicativo está aceitando conexões TCP, datagramas UDP ou associações SCTP nesta porta. Encontrar estas portas é geralmente o objetivo principal do escaneamento.
2. **closed (fechada):** A porta está acessível (recebe e responde a pacotes), mas não há nenhum aplicativo ouvindo nela. Útil para mostrar que um host está ativo.
3. **filtered (filtrada):** O Nmap não consegue determinar se a porta está aberta porque uma filtragem de pacotes impede que as sondas cheguem até ela. Pode ser um firewall dedicado ou de software.
4. **unfiltered (não filtrada):** A porta está acessível, mas o Nmap não consegue determinar se está aberta ou fechada. Usado em escaneamentos ACK.
5. **open|filtered:** O Nmap coloca portas neste estado quando não recebe resposta. O silêncio pode significar que a porta está aberta ou que um firewall descartou o pacote.
6. **closed|filtered:** Usado quando o Nmap não consegue determinar se a porta está fechada ou filtrada.

### Exemplo de Saída do Escaneamento:

```text
Not shown: 995 filtered ports
PORT     STATE  SERVICE
80/tcp   open   http
113/tcp  closed ident
443/tcp  open   https
8080/tcp open   http-proxy
8443/tcp open   https-alt

Nmap done: 1 IP address (1 host up) scanned in 18.57 seconds

```

Para ver um resumo de todos os comandos disponíveis, basta digitar `nmap` sem argumentos no terminal.
