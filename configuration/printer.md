# Configuração de Impressora (CUPS)

Graças ao **CUPS** (Common Unix Printing System), podemos imprimir qualquer documento que desejarmos no Parrot OS.

> **Nota sobre impressoras HP:**
> Estas instruções aplicam-se a qualquer impressora, mas este guia usa uma HP como exemplo. Por esse motivo, se você tem uma HP, pode ser necessário instalar o **HPLIP** (que fornece os drivers necessários) com este comando:
> ```bash
> sudo apt install hplip -y
> ```

## 1. Instalar e Configurar o CUPS

O CUPS já deve vir instalado no ParrotOS, mas se não estiver, abra o terminal e execute:

```bash
sudo apt update && sudo apt install cups

```

### Adicionar usuário ao grupo de administração

Após a instalação, é necessário adicionar seu usuário ao grupo `lpadmin` para realizar tarefas administrativas via interface web. Sem isso, o CUPS não autenticará o usuário.

```bash
sudo adduser user lpadmin

```

> **Importante:** Troque a palavra `user` no comando acima pelo seu **nome de usuário** real do sistema.

### Iniciar o serviço

Certifique-se de que o serviço está rodando:

```bash
sudo service cups start

```

---

## 2. Acessar a Interface Web do CUPS

Agora que os serviços estão ativos, vamos configurar via navegador.
O CUPS é acessível pelo seu navegador favorito no endereço:

👉 **[http://localhost:631/admin](https://www.google.com/search?q=http://localhost:631/admin)**

---

## 3. Adicionando uma Nova Impressora

1. Na interface web do CUPS, clique em **Add Printer** (Adicionar Impressora).
2. Você será solicitado a digitar seu **usuário e senha** (os mesmos que você usa para logar no sistema/sudo).
3. O serviço buscará todas as impressoras locais e de rede.
4. A nova impressora deve aparecer em **Discovered Network Printers**. Selecione-a e clique em **Continue**.

### Personalização e Drivers

5. A próxima página permite personalizar detalhes como **Nome** e **Descrição**.
6. Marque a caixa **Share This Printer** (Compartilhar esta impressora) se quiser que outros clientes na rede possam usá-la. Clique em **Continue**.
7. Agora, selecione o Fabricante (Make) e o Modelo (Model) nas listas ou, se necessário, forneça um arquivo de driver **PPD** específico.
8. Clique em **Add Printer**.

Se tudo for feito corretamente, você verá uma página de confirmação.

---

## 4. Verificar a Instalação

Vamos verificar se a impressora está configurada corretamente.

1. Na interface do CUPS, clique na aba **Printers** (Impressoras) no topo direito.
2. Sua impressora deve aparecer na lista. Clique no nome dela.
3. Nesta página de gerenciamento, você pode ver a fila de impressão e realizar operações de teste.
4. Recomendamos clicar em **Maintenance** > **Print Test Page** para garantir que tudo funciona.

Isso é tudo o que você precisa para configurar uma impressora no ParrotOS!
