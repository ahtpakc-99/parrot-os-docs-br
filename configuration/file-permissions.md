# Permissões de Arquivos e Diretórios

No GNU/Linux, todos os arquivos do sistema pertencem a um **usuário** e a um **grupo**.
* O **dono** (owner) de um arquivo é o usuário que o criou.
* O **grupo principal** deste arquivo é o do usuário que o criou.

Por exemplo, se o usuário `parrot` cria um arquivo, ele pertence ao usuário `parrot` e ao grupo padrão `parrot`. Por essa razão, frequentemente usamos o comando `sudo` para ler, modificar ou executar arquivos de sistema que pertencem ao usuário `root`.

## Analisando Permissões (`ls -l`)
Vamos analisar a saída do comando `ls -l` para entender a estrutura:

```bash
ls -l arquivo.txt
# Saída:
# -rw-rw-r-- 1 parrot hackers    0    oct 16 12:32 arquivo.txt
# drwxr-xr-x 3 parrot hackers  4096   oct 15 16:25 scripts

```

A saída indica o seguinte:

1. **Tipo:** `-` (arquivo) ou `d` (diretório).
2. **Permissões:** `rw-rw-r--` (Explicação detalhada abaixo).
3. **Número de links:** `1` (ou número de arquivos se for diretório).
4. **Dono:** `parrot`.
5. **Grupo:** `hackers`.
6. **Tamanho:** `0` ou `4096` bytes.
7. **Data:** Última modificação.
8. **Nome:** `arquivo.txt`.

### Os Três Tipos de Permissão

O gerenciamento é feito usando um esquema simples de três letras:

* **r** (Read): Permissão de **Leitura**.
* **w** (Write): Permissão de **Escrita** (Modificação).
* **x** (Execute): Permissão de **Execução** (Rodar um programa ou entrar numa pasta).

### Estrutura das Permissões

No exemplo `-rw-rw-r--`, as permissões são divididas em três blocos:

| Dono (Owner) | Grupo (Group) | Outros (Others) |
| --- | --- | --- |
| **rw-** | **rw-** | **r--** |
| Leitura e Escrita | Leitura e Escrita | Apenas Leitura |

### Valor Octal (Numérico)

Para alterar permissões, frequentemente usamos números (soma dos valores):

| Permissão | Letra | Valor Decimal |
| --- | --- | --- |
| Leitura | **r** | **4** |
| Escrita | **w** | **2** |
| Execução | **x** | **1** |
| Nenhuma | **-** | **0** |

**Exemplos de Combinações:**

* `rwx` (4+2+1) = **7** (Controle total)
* `rw-` (4+2+0) = **6** (Ler e escrever)
* `r-x` (4+0+1) = **5** (Ler e executar)
* `r--` (4+0+0) = **4** (Apenas ler)

---

## O Comando `chmod` (Change Mode)

O `chmod` é usado para alterar as permissões.

**Sintaxe Básica:**

```bash
chmod [modo] [arquivo ou diretório]

```

### Método 1: Numérico (Octal)

Imagine que temos uma pasta `scripts/` onde as permissões estão erradas. Queremos que o **Dono** e o **Grupo** tenham controle total (7), mas os **Outros** não tenham acesso nenhum (0).

```bash
chmod -R 770 scripts/

```

* `-R`: Recursivo (aplica a todos os arquivos dentro da pasta).
* `770`: Dono (7), Grupo (7), Outros (0).

**Resultado:**
As permissões mudariam de `-rw-r--r--` para `-rwxrwx---`.

### Método 2: Simbólico (Letras)

Você pode adicionar ou remover permissões usando letras.

* **Quem:** `u` (usuário), `g` (grupo), `o` (outros), `a` (todos/all).
* **Ação:** `+` (adicionar), `-` (remover).
* **Permissão:** `r`, `w`, `x`.

**Exemplos:**

1. **Remover execução de Grupo e Outros:**
```bash
chmod -R og-x scripts/

```


2. **Dar todas as permissões ao Usuário:**
```bash
chmod u+rwx arquivo.sh

```


3. **Adicionar leitura para Todos:**
```bash
chmod +r arquivo.txt

```



---

## O Comando `chown` (Change Owner)

O `chown` altera o **Dono** (e opcionalmente o grupo) de um arquivo ou diretório.

**Sintaxe Básica:**

```bash
chown [opções] [dono]:[grupo] [arquivo]

```

**Opções Principais:**

* `-R`: Altera recursivamente (diretórios e conteúdos).
* `-v`: Verbose (mostra o que está sendo feito).

**Exemplos:**

1. **Mudar Dono e Grupo para `root`:**
```bash
chown -R root:root scripts/

```


*Agora os arquivos pertencem ao usuário `root` e grupo `root`.*
2. **Mudar apenas o Dono para `parrot` (mantendo o grupo atual):**
```bash
chown -R parrot scripts/

```


*Agora os arquivos pertencem ao usuário `parrot`, mas o grupo continua sendo `root` (do comando anterior).*

---

## O Comando `chgrp` (Change Group)

O `chgrp` altera especificamente o **Grupo** de um arquivo. Ele funciona de forma muito similar ao `chown`.

**Sintaxe Básica:**

```bash
chgrp [opções] [grupo] [arquivo]

```

**Exemplo:**
Se um arquivo pertence ao grupo `root` e você quer mudar para o grupo `parrot`:

```bash
chgrp -R parrot scripts/

```

*Isso altera apenas a propriedade do grupo, mantendo o usuário dono inalterado.*
