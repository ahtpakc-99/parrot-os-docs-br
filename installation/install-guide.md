# Guia de Instalação (Passo a Passo)

Este guia irá ajudá-lo a instalar o **ParrotOS** (versão mais recente) em seu computador, passo a passo, através do instalador oficial padrão: **Calamares**.

O instalador é intuitivo e visual, muito semelhante ao de outras distribuições modernas.

## 1. Iniciando a Instalação
Após dar boot pelo Pen Drive e o sistema carregar (Live Mode), você verá um ícone na área de trabalho chamado **"Install Parrot"**.
Clique duas vezes nele para abrir o instalador.

## 2. Seleção de Idioma
A primeira tela solicitará que você escolha o idioma do instalador e do sistema final.
* Procure e selecione **Português do Brasil**.
* Clique em **Próximo**.

![Seleção de Idioma](https://parrotsec.org/docs/img/installation/calamares/1.png)

## 3. Localização (Fuso Horário)
Agora você deve configurar seu fuso horário para que o relógio do sistema fique correto.
* Clique no mapa sobre o Brasil ou selecione **São Paulo** (ou sua região) na lista.
* O idioma e os formatos de número/data serão ajustados automaticamente (pt_BR).
* Clique em **Próximo**.

![Seleção de Localização](https://parrotsec.org/docs/img/installation/calamares/2.png)

## 4. Configuração de Teclado
O instalador tentará detectar seu teclado, mas é importante verificar.
* **Modelo do Teclado:** Geralmente "Generic 105-key PC" funciona bem.
* **Layout:** Selecione **Portuguese (Brazil)**.
* **Variante:** Escolha **Default** (ou teste as teclas como `ç`, `~`, `^` no campo de teste abaixo).

![Configuração de Teclado](https://parrotsec.org/docs/img/installation/calamares/3.png)

## 5. Particionamento de Disco
Esta é a parte mais crítica. Você define onde o Parrot será instalado.

### Opção A: Apagar Disco (Recomendado para iniciantes)
Se você quer que o Parrot seja o **único sistema** no computador.
1. Selecione **Apagar disco**.
2. **Swap (Memória de Troca):**
   * Se tiver SSD: Recomenda-se "Swap to file".
   * Se tiver HD mecânico: Pode usar "Swap with Hibernate" ou "No Swap" se tiver muita RAM (16GB+).

![Apagar Disco](https://parrotsec.org/docs/img/installation/calamares/4.png)

### Opção B: Particionamento Manual
Escolha esta opção apenas se souber o que está fazendo (ex: Dual Boot complexo ou separar a pasta `/home`).
* Você precisará criar pelo menos uma partição raiz (`/`) formatada em **ext4** ou **btrfs**.
* Em sistemas UEFI, precisará de uma partição `/boot/efi` (FAT32).

![Particionamento Manual](https://parrotsec.org/docs/img/installation/calamares/5.png)

## 6. Criando seu Usuário
Configure suas credenciais de acesso.
* **Nome Completo:** Seu nome real (ex: João Silva).
* **Nome de Login:** O nome usado no terminal (ex: `joao`).
* **Nome do Computador:** Como a máquina aparecerá na rede (ex: `parrot-pc`).
* **Senha:** Crie uma senha forte. **Esta será sua senha de ROOT (administrador).**

> **Segurança:** Recomendamos **não** marcar a opção "Entrar automaticamente sem perguntar a senha".

![Criação de Usuário](https://parrotsec.org/docs/img/installation/calamares/6.png)

## 7. Resumo e Instalação
O instalador mostrará um resumo de todas as mudanças que serão feitas.
* Verifique principalmente se o **disco correto** está sendo formatado.
* Se tudo estiver certo, clique em **Instalar**.
* Confirme o aviso final (esta ação não pode ser desfeita).

![Resumo da Instalação](https://parrotsec.org/docs/img/installation/calamares/7.png)

## 8. Finalizando
O processo de instalação começará. Isso pode levar de 5 a 20 minutos dependendo do seu hardware (SSD vs HDD/USB).

Ao finalizar:
1. Marque a caixa **"Reiniciar agora"**.
2. Clique em **Concluído**.
3. Quando a tela ficar preta e pedir, **remova o Pen Drive** e aperte **Enter**.

![Instalação Concluída](https://parrotsec.org/docs/img/installation/calamares/9.png)

---
**Próximo Passo:** [Configuração Pós-Instalação (Updates)](../configuration/system-updates.md)
