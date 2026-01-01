# Partição Persistente (Live USB com Persistência)

Este guia mostra como criar uma partição persistente dentro de um pendrive com o ParrotOS. Isso permite que você salve arquivos e configurações no modo Live USB sem perdê-los ao reiniciar.

Para isso, usaremos a ferramenta **mkusb**.

## 1. Instalando o mkusb

Após baixar o arquivo `.iso` do ParrotOS em nosso site, você precisa baixar o `mkusb`.

1.  Clone o repositório:
    ```bash
    git clone [https://github.com/sudodus/tarballs.git](https://github.com/sudodus/tarballs.git)
    ```

2.  Navegue até a pasta baixada e descompacte o arquivo `dus-plus.tar.xz`:
    ```bash
    cd tarballs && tar -xf dus-plus.tar.xz
    ```
    > **Nota:** Por que usar o `dus-plus.tar.xz` em vez de apenas `dus.tar.xz`? Resumindo, ele contém o pacote `usb-pack-efi` necessário para inicializar a partição em sistemas modernos.

3.  Entre na pasta recém-extraída `dus-plus` e instale a ferramenta digitando:
    ```bash
    cd dus-tplus/ && sudo ./dus-installer i
    ```

4.  Na mesma sessão do terminal, digite `dus` (ou abra o **guidus** no menu do Parrot) para iniciar:
    ```bash
    dus
    ```
    *O programa pode pedir para instalar a interface gráfica `guidus` também. A funcionalidade permanece a mesma.*

---

## 2. Criando a Partição Persistente

Com o mkusb aberto:

1.  Selecione a opção **Install (make a boot device)** (Instalar/Criar dispositivo de boot).
2.  Em seguida, selecione a opção **Persistent-live**.
3.  No menu seguinte, escolha **dus-Persistent** para selecionar o método de criação da partição.
4.  **Selecione o arquivo .iso:** Navegue e escolha a imagem do Parrot que você baixou.
5.  **Selecione o USB:** Escolha o pendrive onde deseja instalar (Recomendamos um pendrive de pelo menos **8 GB** para ter espaço útil de persistência).
6.  Selecione o pacote **upefi** e clique em **OK**.
7.  **Alocação de Espaço:** Uma barra deslizante aparecerá. Defina quanto espaço você deseja dedicar para a persistência (onde seus arquivos ficarão salvos) e quanto ficará para o sistema.
8.  Clique em **Go** para confirmar a operação.

Aguarde alguns minutos. Quando terminar, seu pendrive estará pronto com o ParrotOS e uma partição de dados que salva suas alterações!
