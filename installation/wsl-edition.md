# Instalação no WSL (Windows Subsystem for Linux)

É possível instalar o ParrotOS diretamente dentro do Windows 10 ou 11 usando o WSL. Isso permite rodar ferramentas de Linux sem precisar de uma máquina virtual pesada.

> **Nota:** Atualmente, apenas a **Core Edition** está disponível para WSL.
> Uma versão completa (Security Edition) provavelmente será lançada no futuro. De qualquer forma, **qualquer ferramenta** da Security Edition pode ser instalada manualmente nesta versão usando o comando `apt`.

## 1. Instalando o WSL
Se você já tem o WSL instalado em sua máquina (já usa Ubuntu ou Kali no Windows), pode pular esta seção.

1. Abra o **PowerShell** ou Terminal como Administrador (Botão direito -> Executar como Administrador).
2. Digite o seguinte comando:
   ```powershell
   wsl --install
Se você vir um texto de ajuda, significa que o WSL já está instalado. Caso contrário, aguarde o término da instalação e reinicie o computador se solicitado.

2. Instalando o ParrotOS (Instalação Manual)
Como o Parrot ainda não está na Microsoft Store (Em breve...), precisamos fazer a instalação manual do arquivo.

Baixe o arquivo: Faça o download do arquivo .wsl contendo o sistema na página de downloads do ParrotOS (procure pela seção WSL ou Core).

Execute: Clique duas vezes no arquivo parrot-core_6.x.wsl. Uma janela de instalação aparecerá.

Configure: Digite seu nome de usuário e senha para a conta de usuário Linux.

Notas Importantes
Armazenamento: Seu "Disco Rígido" do WSL será criado como um arquivo .vdhx na mesma pasta onde você executou o instalador. Não delete esse arquivo!

Atualizações: Todas as atualizações podem ser realizadas via sudo apt update && sudo apt upgrade.

Desinstalar/Reinstalar: Se desejar rodar o instalador novamente ou limpar tudo, execute no PowerShell:

PowerShell

wsl --unregister parrot
E depois execute o arquivo .wsl novamente.

3. Solução de Problemas (Troubleshooting)
SystemD (Correção para ferramentas que não iniciam)
Alguns pacotes que requerem o SystemD (como o Powershell Empire ou serviços de banco de dados) não funcionam na instalação padrão do WSL.

Isso pode ser corrigido editando o arquivo de configuração do WSL dentro do Parrot:

No terminal do Parrot, edite o arquivo wsl.conf:

Bash

sudo nano /etc/wsl.conf
Adicione as seguintes linhas ao arquivo:

Ini, TOML

[boot]
systemd=true
Salve o arquivo (Ctrl+O, Enter) e saia (Ctrl+X).

Reinicie sua instância do WSL (feche a janela e abra de novo, ou rode wsl --shutdown no PowerShell).

Bugs Desconhecidos
Se encontrar outros erros, por favor abra uma issue no Projeto GitLab do WSL.
