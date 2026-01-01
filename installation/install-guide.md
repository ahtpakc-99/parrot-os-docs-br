# Guia de Instalação (Passo a Passo)

Este guia irá ajudá-lo a instalar o **ParrotOS** (versão mais recente) em seu computador através do instalador oficial padrão: **Calamares**.

## 1. Iniciando a Instalação
Após dar boot pelo Pen Drive e o sistema carregar (Live Mode), você verá um ícone na área de trabalho chamado **"Install Parrot"**. Clique duas vezes nele.

## 2. Seleção de Idioma
A primeira tela solicitará que você escolha o idioma.
* Procure e selecione **Português do Brasil**.
* Clique em **Próximo**.

## 3. Localização (Fuso Horário)
Agora você deve configurar seu fuso horário.
* Clique no mapa sobre o Brasil ou selecione **São Paulo** (ou sua região) na lista.
* Clique em **Próximo**.

## 4. Configuração de Teclado
O instalador tentará detectar seu teclado.
* **Modelo:** Geralmente "Generic 105-key PC".
* **Layout:** Selecione **Portuguese (Brazil)**.
* **Variante:** Escolha **Default** (teste as teclas `ç`, `~`, `^` no campo de teste abaixo para confirmar).

## 5. Particionamento de Disco
Esta é a parte onde você define onde o Parrot será instalado.

### Opção A: Apagar Disco (Recomendado)
Use esta opção se o Parrot for o **único sistema** no computador. Isso apagará todos os dados do disco.
* Selecione o disco correto (caso tenha mais de um).
* Em **Swap**, recomenda-se "Swap to file" para SSDs.

### Opção B: Particionamento Manual
Use apenas se souber criar partições Linux (`/`, `/boot/efi`, `/home`) manualmente.

## 6. Criando seu Usuário
Configure suas credenciais.
* **Nome de Login:** O nome usado no terminal (sem espaços ou maiúsculas).
* **Senha:** Crie uma senha forte. **Esta será sua senha de ROOT (administrador).**

> **Segurança:** Recomendamos **não** marcar a opção "Entrar automaticamente".

## 7. Instalação
O instalador mostrará um resumo.
* Verifique se o **disco correto** está sendo formatado.
* Clique em **Instalar** e confirme.
* Aguarde o processo (5 a 20 minutos).

## 8. Finalizando
Ao terminar, marque a caixa **"Reiniciar agora"** e clique em **Concluído**. Remova o Pen Drive quando solicitado.

---
**Próximo Passo:** [Configuração Pós-Instalação](../configuration/system-updates.md)
