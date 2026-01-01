# O que é o ParrotOS?

O **Parrot Security** (ParrotOS, Parrot) é uma distribuição GNU/Linux Livre e Open Source baseada no **Debian Stable**, projetada para especialistas em segurança, desenvolvedores e pessoas preocupadas com privacidade.

Ele inclui um arsenal portátil completo para operações de segurança de TI e forense digital. Também inclui tudo o que você precisa para desenvolver seus próprios programas ou proteger sua privacidade enquanto navega na rede.

O Parrot está disponível em três edições principais: **Security**, **Home** e **Architect Edition**. Também está disponível como Máquina Virtual (Virtual Box, Parallels e VMware), em **Raspberry Pi** e também no Docker.

O sistema operacional vem por padrão com o Ambiente de Desktop **MATE**, mas é possível instalar outros ambientes (DEs).

## História e Equipe
O primeiro lançamento público ocorreu em 10 de abril de 2013, como resultado do trabalho de **Lorenzo Faletra**, que continua liderando o desenvolvimento.

Originalmente desenvolvido como parte do *Frozenbox* (um fórum comunitário do mesmo criador do Parrot), o esforço cresceu para incluir uma comunidade de desenvolvedores open source, especialistas em segurança profissional, defensores de direitos digitais e entusiastas de Linux de todo o mundo.

O projeto está sediado em Palermo, Itália, e é governado pela *Parrot Security CIC*, uma empresa de interesse comunitário registrada no Reino Unido.

## Por que "Parrot" (Papagaio)?
Porque nasceu como um jogo.

> *"Todo pirata dos sete mares precisa de um papagaio em seus ombros se quiser abordar os galeões com sua tripulação de filibusteiros."*

## Para quem foi projetado
O sistema é projetado para ser familiar para o especialista em segurança e fácil de usar para o estudante iniciante, mas não tenta esconder seu funcionamento interno como outras distribuições de uso geral tentam fazer.

O Parrot pode ser usado como um **sistema diário**. Ele fornece todos os programas para as tarefas do dia a dia, incluindo uma edição dedicada do sistema (**Parrot Home Edition**) que não inclui ferramentas de segurança ofensiva pré-instaladas.

## Gerenciamento de Software
O sistema possui seu próprio repositório de aplicações, incluindo todos os pacotes suportados pelo Debian, além de muitas outras aplicações e ferramentas que o Debian ainda não pode fornecer. Todos eles são acessíveis diretamente pelo gerenciador de pacotes **APT**.

Além disso, o Parrot suporta:
* **Snap:** Um sistema de distribuição de pacotes que fornece acesso fácil a muitos outros programas que as distribuições GNU/Linux nem sempre enviam em seus arquivos de software.
* **Flatpak:** Uma loja de software universal semelhante ao Snap. Pode ser instalado a partir do repositório oficial do Parrot.
* **Wine:** Uma camada de compatibilidade para rodar aplicações Windows em ambientes GNU/Linux.

---

# Devo usar o Parrot?

## Por que o Parrot é diferente
Mesmo que gostássemos que todos usassem o Sistema Parrot ou, pelo menos, experimentassem, há algumas considerações importantes a fazer sobre quem esperamos que use o Parrot e quem pode ter uma má experiência com ele.

Primeiro de tudo, mesmo que o Parrot forneça versões de uso geral, seu núcleo ainda é ajustado para operações de **Segurança e Forense**. Nesta seção, explicaremos o quão diferente o Parrot é comparado a outras distribuições de uso geral e como ele difere de outras distribuições de Pentest e Forense.

### Distribuições de uso geral
O Parrot é diferente de uma distribuição de uso geral (ex: Ubuntu) porque não tenta de forma alguma esconder seu funcionamento interno.

Isso significa que muitas ferramentas de automação estão incluídas no sistema para torná-lo mais fácil de usar, mas expõem claramente o que o sistema tem "sob o capô".

> **Exemplo:** O *lembrete de atualização do Parrot*. É um programa simples, mas poderoso, que solicita ao usuário verificar atualizações do sistema uma vez por semana. Mas, em vez de esconder o processo de atualização atrás de uma barra de progresso, ele mostra ao usuário o processo completo de atualização a partir da saída do `apt`.

Outra diferença importante é que o Parrot **desativa por padrão todos os serviços de rede** pré-instalados no sistema. Isso serve não apenas para manter um consumo de RAM muito baixo e oferecer melhor desempenho, mas também para evitar a exposição de serviços em uma rede alvo. Cada serviço de rede precisa ser iniciado manualmente quando o usuário precisa dele.

### Distribuições de Pentest
Distribuições de Pentest são famosas por integrar apenas ferramentas de segurança, permitindo acesso root fácil e derrubando todas as barreiras de segurança do sistema que possam influenciar o fluxo de trabalho de um pentester.

O Parrot foi projetado para ser um ambiente muito confortável para especialistas em segurança e pesquisadores. Ele inclui muitos programas básicos para uso diário que as distribuições de pentest geralmente excluem (ao custo de menos de um gigabyte adicional de armazenamento).

Essa escolha foi feita para tornar o Parrot não apenas um bom sistema para realizar testes de segurança, mas também um bom ambiente onde você pode **escrever relatórios, construir suas próprias ferramentas e comunicar-se perfeitamente com colegas de equipe**, sem a necessidade de computadores adicionais, sistemas operacionais extras ou configurações complexas.

Nosso objetivo é permitir que qualquer pentester profissional realize um teste de segurança completo, do início ao relatório final, com apenas uma ISO do Parrot e um notebook comum.

### Distribuições Seguras
O Parrot Security vem com perfis de endurecimento (*hardening*) personalizados e configurações para **AppArmor** e outras tecnologias de segurança Linux. Ele se inspira no sucesso de outros projetos que entregam o mais alto nível de segurança no cenário GNU/Linux, como *Tails* e *Whonix*, para isolar (sandbox) o sistema e entregar uma camada de segurança acima da média.

Toda essa segurança adicional tem um custo: **é mais difícil adotar maus comportamentos no Parrot.**
* Por exemplo, não é possível fazer login como `root` em todo o ambiente de desktop.
* Não é possível iniciar aplicações críticas como navegadores, reprodutores de mídia ou leitores de documentos avançados com permissões privilegiadas desnecessárias.

O usuário ainda pode abrir consoles root, lançar ferramentas de segurança com permissões privilegiadas e usar o sistema sem limites. A única coisa que muda é que todas as aplicações críticas do usuário agora estão protegidas contra maus comportamentos e técnicas comuns de exploit (ou até zero-days), e os danos causados por exploits avançados são muito limitados.

### Distribuições Forenses
Especialistas em forense digital precisam de um ambiente que não comprometa suas evidências.

O Parrot vem com funções de **automount desativadas por padrão**, para permitir que aquisições forenses sejam realizadas de forma segura. A política global de não-montagem automática é configurada de forma redundante em todas as camadas da pilha do sistema, desde a opção de kernel `noautomount` passada por padrão na inicialização, até as configurações específicas do gerenciador de arquivos.

> **Atenção:** Os discos ainda são reconhecidos pelo sistema, e o sistema irá montá-los sem proteções se o usuário abri-los acidentalmente.

O comportamento de não-montagem é consistente e estável, mas nenhuma proteção é fornecida em caso de montagens acidentais. Um bloqueador de escrita (*Write Blocker*) de hardware é sempre recomendado em qualquer cenário de forense digital real.

## Resumo
Em suma, o Parrot é feito para:
* Especialistas em Segurança
* Especialistas em Forense Digital
* Estudantes de Ciência da Computação/Engenharia
* Pesquisadores
* Aspirantes a Hacker (*Wannabe Hackers*)
* Desenvolvedores de Software
