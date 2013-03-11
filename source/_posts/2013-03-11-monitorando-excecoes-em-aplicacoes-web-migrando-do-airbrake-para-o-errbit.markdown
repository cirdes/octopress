---
layout: post
title: "Monitorando exceções em aplicações web: migrando do Airbrake para o Errbit"
date: 2013-03-11 10:04
comments: true
categories: [Ruby on Rails, Heroku]
---

Introdução
----------
----------
Para quem não conhece, algumas ferramentas são capazes de coletar e gerenciar erros em aplicações web. No [Eventick](http://eventick.com.br/), todos os erros são monitorados. Tentamos corrigir e contactar nossos usuários antes deles nos enviarem emails. Existem três ferramentas bem conhecidas que fazem esse trabalho, o [AirBrake](http://airbrake.io/), o [Exceptional](http://www.exceptional.io/) e o [Errbit](https://github.com/errbit/errbit). Nesse post falarei das vantagens do Errbit e como migrar do AirBrake.

AirBrake
--------
--------

O AirBrake é um serviço excelente, ele foi adquirido pelo Exceptional. Os dois serviços apresentam funcionalidades parecidas mas irei limitar-me a falar sobre o primeiro pois foi o serviço que utilizei por pouca mais de um ano.

O principal vantagem do AirBrake é que ele funciona como Software as a Service. Além disso, existe um addon para o Heroku que simplifica sua configuração.
Durante um bom tempo fomos muito felizes com o AirBrake, sem dúvida foi o melhor addon do heroku que utilizamos. Até conhecer o Errbit e concluir que o AirBrake não era tão bom assim. Nesse período de um ano ele mudou pouca coisa.

Problemas
---------
* Preço: O plano básico custa $25 doláres. Não é caro, o problema é pagar $25 e mesmo assim ter menos recursos que uma alternativa gratuita.
* Limitações: Apenas 1 projeto e 1 usuário no plano free.

<!-- more -->

Errbit
------
------

O Errbit é um projeto em rails, open source e 100% compatível com o airbreak. Suporta Ruby on Rails, Python e PHP. Ele apresenta algumas vantagens que me fizeram sair do AirBreak.

![Errbit](/images/post_4/errbit.png "Errbit")

Vantagens
---------

* Intervalo de emails: Por padrão, a cada 1, 10 e 100 erros o errbit envia uma notificação por email. Um erro que aconteceu uma vez provavelmente tem uma prioridade muito menor do que um que já aconteceu 100 vezes.

* Agrupamento de notificações: Permite que notificações similares sejam agrupadas.

* Suporta comentários: É possível adicionar comentários as notificações de erro.

* Backtrace fácil de ler: Ao visualizar o backtrace é possível ir direto para linha de código com erro no github.

* Open source: É uma aplicação rails de código aberto que você pode modificar para atender melhor suas necessidades.

* Free: Ela é gratuita e sem limitações.

* Oauth com github: É possível logar com sua conta do Github

* Javascript: Ela também detecta erros em javascript

Apesar de todas essas vantagens, manter uma máquina virtual com o Errbit é um retrocesso visto que no AirBrake eu não precisava me preocupar com isso. A solução é hospedar no Heroku.

Instalação
----------

* Clonar o projeto

`git clone git://github.com/errbit/errbit.git`

* Criar e configurar uma instância no heroku

`gem install heroku`

`heroku create example-errbit --stack cedar`

`heroku addons:add mongolab:starter`

`heroku addons:add sendgrid:starter`

`heroku config:add HEROKU=true`

`heroku config:add SECRET_TOKEN="$(bundle exec rake secret)"`

`heroku config:add ERRBIT_HOST=some-hostname.example.com`

`heroku config:add ERRBIT_EMAIL_FROM=example@example.com`	

`heroku remote add heroku git@heroku.com:projet-name.git`

`git push heroku master`

* Criar o banco e o usuário padrão

`heroku run rake db:seed --app app-name`

Pronto, seu errbit já está hospedado no heroku. Agora basta entrar nele utilizando o usuário e senha padrão e criar um novo projeto.
Email: demo@errbit-demo.herokuapp.com
Password: password

Com projeto criado, basta adicionar a sua aplicação rails a gem [airbrake_user_attributes](https://github.com/cloudfuji/airbrake_user_attributes) e o arquivo de configuração gerado ao criar um novo projeto.


