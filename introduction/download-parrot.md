# Baixando o Parrot OS

O ParrotOS está disponível para download [no site oficial](https://www.parrotsec.org/download/).
O sistema operacional roda em máquinas mais antigas, mas é recomendado consultar os requisitos do sistema antes de prosseguir.

## Qual versão devo escolher?
O Parrot vem em muitos formatos e tamanhos para atender a todas as necessidades possíveis de hardware e usuários. Dependendo da configuração do seu hardware e do seu objetivo, considere estas opções:

### 🦜 Parrot 6.4 Security Edition (A Completa)
Como o nome sugere, esta é a edição completa.
* **O que é:** Após a instalação, você tem uma estação de trabalho de pentesting completa "pronta para uso", carregada com uma grande variedade de ferramentas.
* **Recomendação:** Altamente recomendado para Desktops e Laptops com pelo menos **4GB de RAM**, para garantir uma experiência fluida durante multitarefas.

### 🏠 Parrot 6.4 Home Edition (A Leve)
Esta versão do Parrot é uma instalação leve que fornece apenas as ferramentas essenciais para começar a trabalhar.
* **O que é:** Ela depende dos mesmos repositórios da Edição Full, permitindo que você escolha a maioria dos programas que deseja instalar posteriormente.
* **Recomendação:** Recomendado para quem está familiarizado com Distros de Pentest, mas requer uma instalação mínima ou quer usar o sistema no dia a dia.

### 🍓 Parrot 6.4 IoT (Raspberry Pi)
Estas são imagens criadas especificamente para dispositivos embarcados.
* **Suporte:** A primeira placa na qual o Parrot pode ser instalado é o **Raspberry Pi** (versões 3, 4/400 e 5). Outras placas seguirão no futuro.

### 🏗️ Parrot 6.4 Architect Edition (Depreciada)
> **Aviso:** Esta edição está marcada como *deprecated* (uso descontinuado/não recomendado).

Esta edição do Parrot não contém nenhum software que você não escolha, pesa cerca de **379 MB** e está disponível para qualquer arquitetura (amd64, i386, arm64).
* **Mac M1/M2:** A versão arm64 também pode ser usada em dispositivos MacOS com processador Apple Silicon (M1/M2) via virtualização (UTM).

---

## Security vs Home vs Architect: Qual escolher?

A **Home Edition** e a **Security Edition** são idênticas no núcleo. A única diferença entre elas é o conjunto de softwares que vem pré-instalado.

* **Home Edition:** Vem sem ferramentas de segurança (apenas navegador, escritório, etc).
* **Security Edition:** Vem com todas as ferramentas de hacking e pentest pré-instaladas.

### Dica Pro: Transformando Home em Security
Você pode usar a Home Edition (para economizar download inicial) e instalar apenas as ferramentas que precisa, ou instalar todas de uma vez com o comando:

```bash
sudo apt install parrot-tools-full

Já a Architect Edition não contém nenhum software pré-instalado. Você decide e personaliza sua edição do ParrotOS logo antes da instalação (requer conexão com internet durante a instalação).

🐳 Parrot 6.4 no Docker
Esqueça tudo o que você sabe sobre as circunstâncias de pentesting. Carregar um laptop para todos os lugares para realizar seu trabalho não é mais obrigatório.

Agora você pode ter um VPS remoto carregado com Parrot OS, pronto para realizar todo tipo de tarefa a partir de um terminal embarcado, com discrição. Esta edição não fornece uma interface gráfica (GUI) por padrão, mas ela está disponível nos repositórios se necessário.

Próximo Passo: Criando um USB Bootável
