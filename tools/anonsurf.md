# AnonSurf (Modo Anônimo)

**AnonSurf** é o wrapper de modo anônimo do Parrot para forçar todas as conexões do sistema a passarem pela rede **Tor**. Ele é escrito na linguagem **Nim** e utiliza bibliotecas GTK, podendo ser usado tanto via Interface Gráfica (GUI) quanto por Linha de Comando (CLI).

Ele vem pré-instalado em ambas as edições principais do ParrotOS (Home e Security).

## 1. Interface Gráfica (GUI)

O AnonSurf pode ser iniciado a partir do menu do Parrot:
* **Caminho:** `Aplicativos` > `Privacidade` > `AnonSurf`.

### Funcionalidades:
* **Start:** Inicia o serviço e redireciona o tráfego.
* **Stop:** Para o serviço e restaura a conexão normal.
* **My IP:** Verifica seu endereço IP atual e detalhes da conexão para confirmar que o anonimato está funcionando.
* **Tor Stats:** Mostra detalhes sobre o uso atual da rede Tor (largura de banda, conexões).
* **Change Identity:** Alterna para um novo "nó de saída" do Tor (mudando seu IP publicamente visível).

---

## 2. Detalhes Técnicos e CLI

### Como funciona?
O AnonSurf funciona manipulando o **iptables** para forçar os aplicativos a usarem a rede Tor.
O `iptables` é um firewall integrado ao kernel Linux. O AnonSurf configura regras para permitir a passagem de pacotes e, em seguida, usa o Tor para realizar o tunelamento de todo o tráfego do usuário de forma anônima (Proxy Transparente).

### Instalação Manual / Compilação
Desde a versão 3.2.0, o AnonSurf foi reescrito com uma nova estrutura de código. Se precisar compilar a versão mais recente manualmente:

1.  **Instale as dependências (Nim e Gintro):**
    ```bash
    sudo apt install nim
    sudo apt install libnim-gintro-dev
    ```

2.  **Baixe, compile e instale:**
    ```bash
    # Supondo que você já clonou ou baixou a fonte
    cd anonsurf/
    make build
    make install
    ```

---

## 3. Sobre o Tor

O Tor é um protocolo de criptografia SOCKS4/SOCKS5. Ele tunela todo o tráfego executado através da rede do usuário anonimamente, ocultando a localização e os dados de rede de qualquer pessoa que esteja monitorando o usuário local ou remotamente.

### Casos de Uso
* Navegação web (Tor Browser).
* Clientes de IRC (como Hexchat).
* Mensagens instantâneas (TorChat).
* Servidores ocultos (Criação de sites `.onion`).

### Funcionamento Técnico do Tor
O protocolo Tor funciona através da **multiplexação** de múltiplos "circuitos" sobre uma única conexão TLS nó-a-nó.

O tráfego do Tor é roteado por **3 nós** por padrão:
1.  **Guard (Guarda):** O nó de entrada.
2.  **Relay (Repetidor):** O nó intermediário.
3.  **Exit (Saída):** O nó final que se conecta à internet aberta.



> **Nota sobre Multiplexação:** Para ser capaz de rotear múltiplos repetidores, o Tor possui "capacidade de multiplexação de fluxo": múltiplas conexões TCP podem ser transportadas sobre um único circuito Tor. Cada nó conhece apenas o par de origem e destino imediato para um circuito; ele não conhece o caminho inteiro.
