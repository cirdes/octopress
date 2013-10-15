---
layout: post
title: "6 ferramentas gratuitas ou de baixo custo fundamentais para CTO's de startups"
date: 2013-10-13 17:34
comments: true
categories: [ferramentas, startup]
---

Introdução
------
------

Para startups ou empresas que estão construindo um produto web, alguns serviços e ferramentas podem facilitar o desenvolvimento, a gestão e o monitoramento do seu produto. Dentro de uma startup, é papel do CTO garantir o bom andamento do desenvolvimento e que a plataforma que está sendo construída tenha a menor quantidade de erros possíveis, além de atender as expectativas de performance.
Ferramentas de baixo custo ou gratuitas podem facilitar bastante esse trabalho, especialmente em pequenas startups onde todo esse trabalho recai sobre apenas uma pessoa. As ferramentas que irei apresentar são as que usamos diariamente no [Eventick](https://www.eventick.com.br/): Github, Trello, Codeship, Errbit, Logentries e Newrelic.

<!-- more -->

Github
------
------

{% img left /images/post_7/github2.png %}

O [Github](https://github.com/) é o maior serviço de repositório de código online, a maioria dos projetos open source estão armazenados no Github. Para projetos open source o Github é gratuito e por apenas 9 dólares mensais é possível ter acesso a até 5 repositórios privados. Ele vai muito além de um simples repositório de código, sendo muito útil para catalogar bugs e ideias para novas funcionalidades como podemos ver no projeto do [Rails](https://github.com/rails/rails/issues) (Veja!). Como no exemplo do Rails, usamos as issues para catalogar bugs e discutir features. Adicionamos tags as nossas issues e agrupamos em milestones para sejam priorizadas e implementadas, servindo assim como um backlog. Assim como nos projetos open source, precisamos saber tudo que é modificado no nosso código e discutir essas mudanças. O Github tem um recurso chamado [Pull Request](https://help.github.com/articles/using-pull-requests), toda nova funcionalidade deve ser submetida para revisão da equipe. Além de garantir que nada indesejado seja colocado no código, permite nivelar a equipe pois todos questionam ou são questionados pelo seu código. Uma alternativa gratuita pode ser o [BitBucket](https://bitbucket.org/)   

Trello
------
------

{% img /images/post_7/trello.png %}

Existem diversas ferramentas para gerenciar atividades mas nenhuma que usei é tão simples e funcional como o [Trello](https://trello.com/). No começo, usávamos post-it colados na parede mas com a necessidade de trabalhar remoto, transferimos nosso quadro para o Trello. Nele, colocamos as atividades do milestone, definido no Github, que estamos trabalhando. É possível criar "cards" que usamos como histórias/features e definir vários estágios por onde nossas histórias passam, desde de um Todo, Doing e Done até um processo mais complexo utilizando [Kanban](http://en.wikipedia.org/wiki/Kanban_(development)). Podemos ver um exemplo do [board de desenvolvimento](https://trello.com/b/nC8QJJoZ/trello-development) do próprio Trello.
O melhor é que isso tudo não custa nada, o Trello é gratuito. 

Codeship
------
------
{% img left /images/post_7/codeship.png %}
Configurar e manter um servidor de [continuous integration](http://en.wikipedia.org/wiki/Continuous_integration) pode ser uma tarefa chata e demora. Quem nunca perdeu horas configurando o [Jenkins](http://jenkins-ci.org/) e depois teve a frustração de ver seu servidor parar de funcionar devido a uma nova dependência que você adicionou ao seu projeto? O [Codeship](http://codeship.io/) é um serviço que custa 9 dólares mensais, ele é bem simples de ser adicionado ao seu projeto. Com o Codeship, uma vez que modificamos o nosso repositório de código, ele detecta essa modificação, baixa a nova versão e executa todos os testes automatizados. Caso os testes passem, ele faz o deploy para o servidor de homologação do Eventick. Caso os testes falhem, ele envia um email mostrando quais testes não passaram e quem foi o responsável por quebrá-los. Para mais informações sobre Continuios Integration eu recomendo esse [texto](http://www.martinfowler.com/articles/continuousIntegration.html#BenefitsOfContinuousIntegration) de Martin Fowler

Errbit
------
------
{% img /images/post_7/errbit.png %}
O [Errbit](https://github.com/errbit/errbit) talvez seja a ferramenta mais importante, com ele é possível monitorar os erros da sua aplicação. Por mais que se escrevam testes ou tenha-se um controle rigoroso de qualidade, ninguém está livre de erros. Nem mesmo empresas como Google ou Apple estão imunes a falhas. O Errbit permite detectar um erro sem a necessidade do usuário ter que reportá-lo, seja esse erro no backend da sua aplicação ou no seu código javascript rodando no cliente. O Errbit é um projeto open-source que tive a oportunidade de contribuir, em outro [post](http://cirdes.com.br/blog/2013/03/11/monitorando-excecoes-em-aplicacoes-web-migrando-do-airbrake-para-o-errbit/) que fiz é possível encontrar um passo a passo de como configurá-lo. Como alternativas temos o [AirBrake](http://airbrake.io/) e o [Exceptional](http://www.exceptional.io/) que são pagos.

Logentries
------
------
{% img /images/post_7/logentries.png %}

O [Logentries](https://logentries.com/) é uma ferramenta que permite analisar o log das nossas aplicações web. Na maioria das vezes não damos importância ao log, mas ele é o registro de tudo que acontece no nosso sistema. Já precisamos analisar eventos que ocorreram uma semana atrás para entendermos o comportamento do sistema. Nesses casos, é fundamental ter um serviço como o Logentries que nos permite extrair informações com facilidade. O Logentries tem um plano gratuito. Como alternativas temos os [Papertrail](https://papertrailapp.com/) e o [Loggly](http://www.loggly.com/).

NewRelic
------
------

{% img left /images/post_7/newrelic.png %}
Mesmo que você tenha uma plataforma livre de erros, saber como ela está se comportando em termos de performance é fundamental. O tempo de resposta está diretamente ligada a satisfação do usuário. De acordo com [pesquisas:](http://alistapart.com/article/improving-ux-through-front-end-performance), 

* Adicionar meio segundo ao tempo de carregamento de uma página de resultados de busca pode diminuir o tráfego e os lucros com publicidade em 20%, segundo estudo do Google.

* A Amazon percebeu que a cada 100 milissegundos adicionais de carregamento de suas páginas, as vendas caíam 1%.

* Os usuários esperam que as páginas carreguem em 2 segundos – e depois de 3 segundos, quase 40% dos usuários vai simplesmente sair.

Sabendo o quão importante é performance, precisamos monitorar o desempenho da nossa aplicação. O [NewRelic](http://newrelic.com/) oferece ótimas ferramentas para isso, semanalmente ele envia informações de tempo médio de carregamento de página. Ele permite que você analise sua aplicação em termos de processamento no servidor e tempo de renderização no navegador separadamente. Sabemos que [otimização prematura](http://c2.com/cgi/wiki?PrematureOptimization) pode matar o seu negócio, o NewRelic leva em consideração o tempo e o número de vezes que uma requisição é executada. Uma requisição que só é executava uma vez ao dia, mesmo que seja lenta,  não precisa ser otimizada.
O NewRelic tem uma versão gratuita que é limitada, o ideal é pagar pelo NewRelic apenas quando é preciso focar em otimização.

Por fim
-------
-------

Se alguém discorda ou conhece alguma ferramenta útil que não foi citada, aproveite para deixar um comentário. :) 

