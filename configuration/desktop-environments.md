# Ambientes de Desktop (DE)

O ParrotOS vem com o **MATE Desktop Environment** como padrão para todas as edições (Home, Security e HTB). No entanto, ambientes de desktop adicionais podem ser instalados no sistema.

Cada DE (Desktop Environment) tem suas próprias características, mas recomendamos que você experimente antes de decidir qual instalar definitivamente. Como a DE é a interface gráfica através da qual o usuário interage com o sistema operacional, existem muitas maneiras de modificar seus vários componentes.

Os seguintes ambientes estão disponíveis em nosso repositório e oferecem total possibilidade de personalização:
* **MATE** (Padrão: Leve e clássico)
* **XFCE** (Muito leve e modular)
* **GNOME** (Moderno e workflow diferente)
* **KDE Plasma** (Altamente personalizável e visual moderno)

> **Nota sobre i3:** Se você prefere um *Window Manager* (Gerenciador de Janelas em mosaico) em vez de uma DE completa, adicionamos um metapacote ao nosso repositório para instalar o **i3**.

A diferença entre as DEs diz respeito principalmente à interface gráfica; todo o software (ferramentas de hacking, editores, etc.) está disponível nos repositórios do Parrot, independentemente da DE utilizada.

---

## Como Instalar um Ambiente de Desktop

Para instalar uma nova interface, basta digitar no terminal o seguinte comando, substituindo `<desktop environment>` pelo nome desejado (ex: `mate`, `kde`, `xfce`, `gnome`):

```bash
sudo apt update && sudo apt install parrot-desktop-<desktop environment>

```

*Exemplo para instalar o KDE:* `sudo apt install parrot-desktop-kde`

### Como Trocar de Ambiente (Sessão)

Após a instalação:

1. **Reinicie** o computador.
2. Na tela de login, antes de digitar a senha, procure por um ícone de sessão (geralmente um **ponto branco ⚪️** ou uma engrenagem próxima ao nome de usuário).
3. Clique nele e selecione a nova DE que você instalou.
4. Faça o login normalmente. Você agora usará a nova interface com todas as suas ferramentas e configurações anteriores preservadas.

> **⚠️ Recomendação:**
> Você pode instalar mais de uma DE, mas considerando a grande quantidade de pacotes e bibliotecas que cada uma traz, **recomenda-se manter apenas uma ou no máximo duas** instaladas para evitar conflitos de sistema e poluição de menus.
