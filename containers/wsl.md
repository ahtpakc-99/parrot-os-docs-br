# Edição WSL (Windows Subsystem for Linux)

Instale o ParrotOS no WSL (Subsistema Windows para Linux).

* **Compatibilidade:** Compatível com as versões mais recentes do **Windows 10** e **Windows 11**.
* **Edição:** Atualmente, apenas a **Core Edition** está disponível. Uma Security Edition completa provavelmente será lançada no futuro.
* **Nota:** De qualquer forma, **qualquer ferramenta** da Security Edition pode ser instalada manualmente usando o `apt`.

## 1. Instalando o WSL

Se você já tem o WSL instalado em sua máquina, **pode pular esta seção**.

1.  Abra um PowerShell ou Terminal como administrador (Botão direito -> Executar como Administrador).
2.  Digite o comando:
    ```powershell
    wsl --install
    ```
3.  Se você vir um texto de ajuda, significa que o WSL já está instalado. Caso contrário, aguarde o término da instalação.

---

## 2. Executando o ParrotOS WSL

### Instalação Manual
Como a versão da Microsoft Store ainda está "Em breve", utilizamos o método manual.

1.  **Download:** Baixe o arquivo `.wsl` contendo os arquivos necessários na [página de downloads do site do ParrotOS](https://parrotsec.org/download/).
2.  **Executar:** Clique duas vezes no arquivo `parrot-core_6.4.wsl` (ou versão correspondente) e uma janela de instalação aparecerá.
3.  **Configurar:** Agora, digite seu nome de usuário e senha para sua conta de usuário Linux.

### Notas Importantes
* **Armazenamento:** Seu "Disco Rígido" do WSL será criado como um arquivo `.vdhx` na mesma pasta onde você criou/executou o iniciador.
* **Atualizações:** Todas as atualizações podem ser realizadas via comando padrão `apt update` e `apt upgrade`.
* **Resetar/Reinstalar:** Se você deseja rodar o instalador novamente (começar do zero), você deve executar no PowerShell:
    ```powershell
    wsl --unregister parrot
    ```
    E depois executar o arquivo `.wsl` novamente.

### Microsoft Store
*Em breve...*

---

## 3. Solução de Problemas (Troubleshooting)

### Pacotes exigindo SystemD
Pacotes que requerem o **SystemD** (ex: Powershell Empire) não funcionam nas instalações padrão do WSL.

Isso pode ser corrigido editando o arquivo `/etc/wsl.conf` dentro do Parrot e adicionando as seguintes linhas:

```ini
[boot]
systemd=true


Após salvar, reinicie sua instância do WSL (feche a janela e abra novamente ou use wsl --shutdown no Windows).

Problemas Desconhecidos
Por favor, abra uma issue no Projeto GitLab do WSL para quaisquer bugs que você encontrar.
