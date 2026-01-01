# Comunidade e Contribuidores

O Parrot nasceu e continua sendo um projeto totalmente **open-source**. Isso significa que qualquer pessoa pode ver o código de cada um de seus componentes e, se tiver interesse, modificá-lo.

Se você gosta do mundo open source e, em particular, do projeto Parrot, você está fortemente convidado a contribuir. Aqui você encontrará um guia sobre como proceder e em quais projetos você pode contribuir atualmente.

Não importa o quão bom você seja tecnicamente em uma determinada área, você verá que pode contribuir de várias maneiras, dependendo do subprojeto do Parrot. Qualquer contribuição motivada e útil é sempre mais do que bem-vinda.

> Atualmente, todos os pacotes Debian e todas as ferramentas desenvolvidas pela equipe Parrot residem no [GitLab](https://gitlab.com/parrotsec) e no [GitHub](https://github.com/parrotsec) (como um espelho de backup).

## Por que ser um contribuidor?
Ser um contribuidor de um projeto open source significa que você tem a chance de:

1.  **Conhecer novas pessoas:** Você poderá conhecer muitos desenvolvedores como você, apaixonados pelo mundo dos projetos open-source. Isso não só ajudará você a expandir sua rede profissional (*networking*), mas também a fazer amizades verdadeiras.
2.  **Aprender e ensinar coisas novas:** A primeira regra do contribuidor é "nunca fique preso no que você já sabe". Não importa se você é um novato ou um desenvolvedor sênior, se começar a contribuir, aprenderá muito. Por outro lado, terá a chance de ensinar coisas novas a outras pessoas (isso aumentará muito sua confiança, acredite em nós).
3.  **Valorizar seu trabalho:** Você terá a chance de testar antecipadamente alguns de nossos pacotes e, no melhor cenário, seu trabalho será incorporado ao Parrot Security OS.

## Trabalhando em um subprojeto
Como trabalhamos principalmente no GitLab, é importante que você tenha uma conta registrada lá para começar.

Uma vez escolhido o subprojeto, entre em contato com a equipe pelo e-mail `team@parrotsec.org`, especificando o projeto escolhido e a parte em que deseja contribuir.

Atualmente, é possível contribuir nos seguintes subprojetos:

### 1. Website
O site do Parrot (`parrotsec.org`) foi construído usando o framework **NextJS** e a biblioteca **React**. Você é livre para visualizar e analisar o código clonando o repositório. O mantenedor revisará sua solicitação de merge o mais rápido possível.

### 2. Documentação
A documentação oficial (`parrotsec.org/docs`) é baseada no framework **Docusaurus v2**. Se você acha que pode adicionar documentos essenciais ou interessantes, sinta-se à vontade para clonar o repositório e abrir um *merge request*.

### 3. Pacotes Debian
A maioria dos nossos programas de terceiros e pré-incluídos vem do Debian. Você pode contribuir criando novos pacotes Debian ou propondo novas ferramentas, estritamente já empacotadas de acordo com os padrões Debian.
* Inicialmente, o trabalho deve ser iniciado em um repositório pessoal fazendo um *fork* do pacote.
* Uma vez que o código esteja configurado corretamente, abra um merge request.

### 4. Comunidade (Moderadores)
A comunidade é uma parte muito importante para um sistema operacional como o Parrot. Sempre precisamos de novos moderadores para canais do Discord, nosso Fórum e grupos do Telegram.

---

## Estrutura da Comunidade
Cada comunidade é dividida nas seguintes seções:

* **General:** Um local de boas-vindas. Sinta-se à vontade para pedir ajuda ou o que precisar.
* **Support:** Sala de Suporte Técnico para o ParrotOS.
* **Ask the Devs:** Os desenvolvedores do ParrotOS estão aqui para responder perguntas sobre o SO e mais.
* **Distro Development:** Notícias e prévias do progresso do desenvolvimento da próxima versão.
* **Hacking:** Divirta-se fazendo perguntas sobre técnicas de hacking, leia experiências de usuários ou discuta sobre Segurança em geral.
* **Programming:** Discussões sobre programação são altamente encorajadas.
* **Sysadmin:** Administração de sistemas, redes, hardware e software.
* **OffTopic:** Sala de conversa livre (memes são bem-vindos!).
* **News:** Canal oficial para obter as últimas notícias sobre o Parrot.

## Manifesto da Comunidade
Encorajamos fortemente os usuários a engajar discussões não apenas para suporte, mas também para qualquer assunto relacionado a segurança, hacking e programação.

Para manter nossa comunidade saudável, pedimos que siga certos requisitos:

### Seja gentil, sempre.
É importante manter um comportamento consistentemente educado e paciente com os usuários. Reserve a frustração para circunstâncias verdadeiramente excepcionais.

### Respeite a Todos.
Nossa comunidade deve ser saudável mesmo quando se trata de religião, crença política, deficiências ou comunidades LGBT+. Não espalhe ódio sobre nada nem ninguém.

### Seja um guia para iniciantes.
Ninguém nasce um especialista. Não tome nada como garantido. Se um usuário fizer uma pergunta sobre algo que você sabe muito bem, compartilhe seu conhecimento. Se não souber a resposta, guie o usuário gentilmente para esperar alguém mais experiente.

### Esteja sempre entusiasmado para aprender.
O conhecimento está em constante evolução. Confronte a comunidade o máximo possível para aprender novas possibilidades.

### Evite agir impulsivamente.
Todos podem ter gostos e desgostos, mas isso não deve afetar a comunidade. Modere com inteligência e raciocínio, não com suas emoções pessoais.

---

## Fluxo de Desenvolvimento
Nosso fluxo de trabalho de desenvolvimento é baseado nos seguintes pontos:

1.  Desenvolvedores escrevem seu código e fazem um primeiro teste local para resolver o máximo de bugs possível.
2.  Enviam a primeira versão (ou atualização) no GitLab. O Líder da Equipe analisa e aprova.
3.  Uma campanha beta aberta/interna é lançada para investigar o código e encontrar bugs/vulnerabilidades.
4.  Se bugs forem descobertos, os passos anteriores se repetem.
5.  Quando o código está pronto para ser empacotado, o Líder da Equipe aceita as modificações finais.
