# Verificação de Hash e Chaves

## Por que verificar chaves e assinaturas?
A maioria das pessoas — até mesmo programadores — se confunde com os conceitos básicos subjacentes às assinaturas digitais. Portanto, recomendamos a leitura desta seção, mesmo que pareça trivial à primeira vista.

As assinaturas digitais podem provar tanto a **autenticidade** quanto a **integridade** com um grau razoável de certeza.
* **Autenticidade:** Garante que um determinado arquivo foi de fato criado pela pessoa que o assinou (ou seja, não foi forjado por terceiros).
* **Integridade:** Garante que o conteúdo do arquivo não foi adulterado (ou seja, que um terceiro não alterou seu conteúdo de forma indetectável durante o trânsito).

> **Importante:** Assinaturas digitais não provam que o arquivo não é malicioso. Nada impede alguém de assinar um programa malicioso. O ponto é decidir em quem confiamos (ex: Linus Torvalds, Microsoft ou o Projeto Parrot) e assumir que, se o arquivo foi assinado por eles, não deve ser malicioso.

Ao verificar os arquivos que baixamos, eliminamos preocupações sobre ataques de "Man-in-the-Middle", espelhos comprometidos, ataques de Wi-Fi ou funcionários desonestos em provedores de hospedagem.

No entanto, para que a verificação faça sentido, devemos garantir que a **Chave Pública** que usamos para verificar a assinatura é, de fato, a original do Projeto Parrot.

---

## 1. Obter a Chave e Verificar Repositórios

Se você não está familiarizado com o GnuPG ou se nunca configurou isso antes, siga os passos abaixo. Isso corrigirá eventuais avisos de "unsafe ownership".

1.  **Inicialize o GnuPG e ajuste permissões:**
    ```bash
    chmod --recursive og-rwx ~/.gnupg
    ```

2.  **Baixe e importe a chave do ParrotOS:**
    ```bash
    wget -q -O - [https://deb.parrotsec.org/parrot/misc/parrotsec.gpg](https://deb.parrotsec.org/parrot/misc/parrotsec.gpg) | gpg --import
    ```

> **Aviso de Segurança:** Verificar o *timestamp* (carimbo de data/hora) da assinatura faz sentido. Por exemplo, se você viu anteriormente uma assinatura de 2024 e agora vê uma de 2023, isso pode ser um ataque direcionado de rollback (downgrade) ou congelamento indefinido.

---

## 2. Verificação da ISO (Hash)

Depois de baixar a ISO, é crucial verificar se o arquivo baixado é idêntico ao original.

### Verificação MD5
1.  Acesse a lista de hashes assinados: [https://download.parrot.sh/parrot/iso/6.4/signed-hashes.txt](https://download.parrot.sh/parrot/iso/6.4/signed-hashes.txt)
2.  Na seção "MD5", encontre o hash que corresponde à ISO que você baixou.
3.  Abra o terminal na pasta onde está a ISO e execute (exemplo com a versão Home):
    ```bash
    md5sum Parrot-home-6.4_amd64.iso
    ```
4.  **Compare:** O terminal irá gerar uma string alfanumérica.
    * Copie essa string gerada.
    * Vá no navegador onde abriu o `signed-hashes.txt`.
    * Aperte `CTRL + F` e cole o hash.
    * Se corresponder exatamente, o arquivo está íntegro.

> **Se os hashes não baterem:** Houve um problema no download ou no servidor. Baixe novamente (preferencialmente de outro espelho/mirror).

### Outros Hashes (SHA256 / SHA512)
O método é exatamente o mesmo, apenas mudando o comando para o tipo de hash desejado. O SHA512 é mais seguro que o MD5.

**Exemplo com SHA512:**
```bash
sha512sum Parrot-home-6.4_amd64.iso

```

Compare o resultado com a seção SHA512 do arquivo de texto linkado acima.
