# O que é GNU/Linux?

GNU/Linux é um sistema operacional construído ao longo dos anos graças às contribuições de muitos desenvolvedores ao redor do mundo. Algumas de suas peculiaridades serão descritas aqui.

## Software Livre (Free Software)
"Software livre" é o software que respeita a liberdade dos usuários e de sua comunidade. Em termos gerais, significa que os usuários têm a liberdade de executar, copiar, distribuir, estudar, modificar e melhorar o software.

Em outras palavras, "software livre" é uma questão de **liberdade**, não de preço. Para entender o conceito, pense em "livre" como em "liberdade de expressão" (*free speech*), não como em "cerveja grátis" (*free beer*).

Em inglês, às vezes no lugar de "free software" dizemos "libre software", usando esse adjetivo de origem latina derivado de "liberdade", para mostrar que não queremos dizer que o software é necessariamente gratuito (sem custo).

### As Quatro Liberdades
Existem quatro liberdades que definem o "Software Livre":

* **Liberdade 0:** A liberdade de executar o programa como desejar, para qualquer propósito.
* **Liberdade 1:** A liberdade de estudar como o programa funciona e alterá-lo para fazer o que você deseja. O acesso ao código-fonte é uma condição necessária para isso.
* **Liberdade 2:** A liberdade de redistribuir cópias.
* **Liberdade 3:** A liberdade de distribuir cópias de suas versões modificadas para terceiros. Isso permite que você ofereça a toda a comunidade a oportunidade de se beneficiar das modificações. O acesso ao código-fonte é uma condição necessária para isso.

Um programa é "software livre" se ele concede adequadamente aos usuários todas essas liberdades. Caso contrário, não é livre; diz-se que é "Software Proprietário".

> **Resumo:**
> * "Software Livre" não significa necessariamente que é de graça, embora em muitos casos seja.
> * Ele fornece quatro liberdades básicas: executar, modificar/estudar, redistribuir e distribuir modificações.

Você pode ler mais sobre isso no link: [Filosofia GNU](https://www.gnu.org/philosophy/free-sw.en.html)

## O Projeto GNU
Vamos começar com um pouco de história... Estamos na década de 70 do século 20, quando um homem chamado **Richard Stallman** começou a trabalhar no MIT (Massachusetts Institute of Technology).

Nessa época, era muito comum trabalhar com software livre. Os programadores eram livres para cooperar entre si e o faziam com frequência. Além disso, até as empresas de computadores distribuíam seu software livremente. Tudo isso mudou na década de 1980, e praticamente todo o software começou a ser distribuído de forma privada (fechada), o que significa que tal software tinha donos que proibiam a cooperação entre usuários.

Por esse motivo, e diante do que parecia uma injustiça, Richard Stallman decide criar o **projeto GNU** em 1983. Em 1985, a **Free Software Foundation (FSF)** foi fundada com o objetivo de arrecadar fundos para ajudar a programar o GNU.

### O Significado de GNU
O sistema operacional GNU é um sistema de software livre completo compatível com Unix. O termo GNU vem de **"GNU is Not Unix"** (GNU Não é Unix). É um acrônimo recursivo.

Richard Stallman escreveu o anúncio inicial do Projeto GNU em setembro de 1983. Uma versão estendida, chamada [Manifesto GNU](https://www.gnu.org/gnu/manifesto.html), foi publicada em setembro de 1985.

O nome "GNU" foi escolhido porque atendia a alguns requisitos:
1.  Era um acrônimo recursivo.
2.  Era uma palavra real.
3.  Era divertido de dizer (ou cantar).

Eles decidiram tornar o sistema operacional compatível com Unix porque o design geral já estava testado e era portável, e porque a compatibilidade tornava fácil para os usuários de Unix migrarem para o GNU.

No início de 1990, os principais componentes já haviam sido encontrados ou programados, exceto um: **o kernel**.

## O Projeto Linux
Vamos pular na história, desta vez para 1991.

Por volta dessa época, um estudante de ciência da computação finlandês chamado **Linus Torvalds** queria criar um sistema operacional semelhante ao Minix (que ele usava na universidade), mas que funcionasse em seu novo computador com processador 80386.

Usando o compilador GNU C, Linus Torvalds logo teve uma primeira versão do Kernel capaz de rodar em seu computador. Em 25 de agosto de 1991, ele anunciou esse sistema na Usenet, na lista `comp.os.minix`. Seu projeto rapidamente ganhou seguidores e muitos se juntaram a ele, começando a desenvolver para o referido Kernel.

Linus inicialmente lançou seu software sob sua própria licença, embora tenha finalmente escolhido a licença **GNU GPL** em 1992, em parte porque a ferramenta C que ele havia usado para compilá-lo também era GPL.

### A Origem do Nome "Linux"
O nome Linux, para este kernel, foi adotado meses após sua publicação, já que o próprio Linus queria originalmente chamá-lo de **"Freax"**. De fato, na primeira versão do kernel, você pode ver dentro do `makefile` que ele o chamava assim.

Finalmente, Ari Lemmke, que era uma das pessoas responsáveis pelo servidor FTP na Universidade de Tecnologia de Helsinque, colocou os arquivos no servidor sob o projeto "Linux" sem consultar Linus. Linus não gostou desse nome porque o achou muito egocêntrico. Ele acabou concordando com a mudança de nome e, muito tempo depois, em uma entrevista, o próprio Linus comentou que "foi simplesmente o melhor nome que poderia ter sido escolhido".

## GNU/Linux (A União)
A FSF (GNU) estava desenvolvendo um kernel chamado **Hurd** (ainda em desenvolvimento). Esse kernel estava se desenvolvendo mais lentamente do que eles imaginavam. Então, antes do lançamento do kernel Linux, ele foi adotado dentro do projeto.

Portanto, o nome correto para o Sistema Operacional não é apenas Linux, mas **GNU/Linux**. Hoje em dia, quando as pessoas falam sobre Linux, elas estão realmente falando sobre GNU/Linux.

O kernel por si só é inútil para o usuário comum. O kernel é o componente que faz o software e, portanto, o usuário, ser capaz de se comunicar com o hardware. Mas é preciso mais do que um kernel para rodar um computador. É necessário que existam certos programas na parte do usuário (userland). Esses programas podem ou não ser licenciados sob a GPL (GNU).
