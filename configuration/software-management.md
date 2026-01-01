### Gerenciamento de Software (APT)

Neste capítulo, apresentaremos o gerenciador de pacotes **apt** do Parrot.

## Conceitos Básicos
Um programa é uma série de instruções escritas em linguagens de programação como C, Go, Nim ou Rust. Essas instruções são armazenadas em arquivos de texto chamados **fontes** (source code). Para funcionar em nossos sistemas, eles devem ser convertidos em linguagem de máquina. Esse passo é chamado de **compilação**. A compilação gera um ou vários arquivos, compreensíveis pelo sistema, chamados **binários**.

O usuário não precisa compilar as fontes de cada programa, pois os desenvolvedores são responsáveis por compilar e gerar os respectivos binários. Um programa pode conter não apenas o executável, mas uma série de arquivos. Os desenvolvedores combinam esse software em um arquivo chamado **pacote**.
* **Formatos Comuns:** Dois dos mais conhecidos são `.rpm` (Red Hat) e `.deb` (Debian).
* **Parrot:** O Parrot usa o formato `.deb`.

### Dependências
Para compilar programas, frequentemente são necessárias bibliotecas de terceiros. Se tentássemos compilar um programa manualmente, teríamos que instalar essas "dependências" antes. Da mesma forma, para instalar um binário pronto, precisamos ter instalado as dependências necessárias para seu funcionamento correto.

Para gerenciar essas dependências e a instalação de pacotes, foram criados os **gerenciadores de pacotes**. O Parrot utiliza um dos mais famosos, criado pelos desenvolvedores do Debian: o **apt**.

As principais funções de um gerenciador de pacotes são:
* Busca de software
* Instalação de software
* Atualização de software e do sistema
* Gerenciamento de dependências
* Remoção de software

---

## Lista de Repositórios

O gerenciador de pacotes deve verificar em um local específico (pode ser um diretório local ou um endereço de rede) a disponibilidade do software. Esses locais são chamados de **repositórios**.

Embora no Parrot não seja necessário (nem recomendado) adicionar novos repositórios ou modificar os existentes, é bom saber onde configurá-los. No sistema de arquivos, o arquivo principal fica em `/etc/apt/sources.list.d/parrot.list`.

O conteúdo deste arquivo deve ser:

```bash
# stable repository
deb [http://deb.parrot.sh/parrot](http://deb.parrot.sh/parrot) lory main contrib non-free non-free-firmware
#deb-src [http://deb.parrot.sh/parrot](http://deb.parrot.sh/parrot) lory contrib non-free non-free-firmware

```

Com isso, garantimos a lista de repositórios correta, onde os desenvolvedores do Parrot mantêm os pacotes atualizados.

---

## Comandos do Gerenciador de Pacotes

O gerenciador de pacotes do Parrot é o `apt`. Entre outras coisas, ele é responsável por instalar pacotes, verificar dependências e atualizar o sistema.

Abaixo estão as opções mais comuns:

### Busca e Informação

**Procurar um pacote ou termo:**

```bash
apt search <pacote/termo>

```

**Mostrar informações detalhadas de um pacote:**

```bash
apt show <pacote>

```

**Mostrar dependências de um pacote:**

```bash
apt depends <pacote>

```

**Listar todos os pacotes instalados no sistema:**

```bash
apt list --installed

```

### Instalação e Remoção

**Instalar um pacote:**

```bash
apt install <pacote>

```

**Desinstalar um pacote:**

```bash
apt remove <pacote>

```

**Deletar um pacote incluindo seus arquivos de configuração (Purge):**

```bash
apt purge <pacote>

```

**Deletar automaticamente pacotes não utilizados:**

> **Cuidado:** Devido à complexidade de dependências, este comando pode deletar pacotes indesejados se não for verificado com atenção.

```bash
apt autoremove

```

### Atualização

**Atualizar a lista de repositórios (Baixar informações):**

```bash
apt update

```

**Atualizar um pacote específico para a última versão:**

```bash
apt upgrade <pacote>

```

**Atualizar a distribuição completa (Recomendado):**
Este comando atualizará seu sistema para a próxima versão disponível de forma segura.

```bash
sudo parrot-upgrade

```

### Limpeza

**Limpar caches e pacotes baixados:**

```bash
apt clean && apt autoclean

```

*Estes são apenas alguns exemplos. Se precisar de mais informações, consulte a página de manual digitando `man apt` no terminal.*
