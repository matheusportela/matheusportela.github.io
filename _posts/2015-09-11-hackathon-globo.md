---
layout: post
status: publish
published: true
title: Hackathon Globo
date: '2015-09-11 15:08:14 +0000'
date_gmt: '2015-09-11 18:08:14 +0000'
categories:
- Innovation
tags:
- hackathon
- myo
- gopro
- arduino
- hardware
- hacking
- software
- maestro
comments: []
---
Nesse fim de semana, fui convidado para participar do [1º Hackathon Globo](http://hackathonglobo.com/) e essa foi uma das experiências mais incríveis que já tive. Para quem nunca ouviu falar, ["hackathon"](https://en.wikipedia.org/wiki/Hackathon) é um tipo de evento no qual pessoas reúnem-se para criar tecnologia em pouquíssimo tempo, em geral de 24 a 48 horas. Algo como uma maratona de criação de tecnologias. Obviamente, isso inclui noites **não**-dormidas e altos níveis de estresse.

O Hackathon Globo teve cerca de 1800 inscritos, dos quais 40 foram selecionados para participar. Durante 33 horas, os grupos formados deveriam criar novas tecnologias de acordo com o seguinte tema:

> Como a tecnologia pode mudar a forma de produzir e consumir conteúdo?

Organizado pela [Rede Globo](http://www.globo.com.br), o evento ocorreu dentro da casa do [Big Brother Brasil](http://gshow.globo.com/realities/bbb/) (sim, a casa dos "brothers") e contou com participantes de diversas partes do Brasil, desde Pernambuco até o Rio Grande do Sul. Pela primeira vez, a casa do BBB foi utilizada para fins diferentes de gravar o programa, então foi um privilégio entrar na casa (ainda mais com pessoas tão inteligentes quanto foram).

<center><figure><img src="/assets/images/casa_bbb.jpg"/><figcaption>A famosa piscina do BBB</figcaption></figure></center>

A minha maior surpresa, ao entrar na casa, foi ver a quantidade de equipamentos de alta tecnologia que estavam disponíveis para utilizarmos durante o Hackathon: sensores, motores e até robôs! Além disso, a equipe de Pesquisa e Desenvolvimento da Globo estava sempre à disposição para tirar todas as nossas dúvidas.

<center><figure><img src="/assets/images/equipamentos.jpg"/><figcaption>GoPro, Myo, Kinect, Oculus Rift e outros</figcaption></figure></center>

Após avaliar todas as possibilidades, montamos nossos grupos de trabalho. O grupo 3 foi composto pelos incríveis e ultracompetentes Vitor Meriat, Daniel Buckentin, Luan Andrade, Fabiano Monte e eu, Matheus Portela. Nossa proposta consistiu em desenvolver um sistema que possibilitasse repórteres controlarem posições de câmeras à distância. Assim, mesmo se o reporter estiver sozinho em um local isolado, ele será capaz de criar reportagens com câmeras dinâmicas e *takes* mais interessantes. O projeto foi carinhosamente apelidado **Maestro**, em referência aos movimentos manuais executados pelo regente ao conduzir uma orquestra.

<center><figure><img src="/assets/images/equipe_3.jpg"/><figcaption>A super competente equipe 3</figcaption></figure></center>

Para isso, utilizamos diversas tecnologias diferentes:

* [Myo](http://www.myo.com/): sensor de movimentos da mão para possibilitar acionamento à distância
* [GoPro](http://gopro.com/): câmera portátil para captar imagens e vídeos
* [Arduino](https://www.arduino.cc/): microcontrolador para acionar os motores e alterar a posição das câmeras
* [Node.js](https://nodejs.org/en/): utilizado para streaming de vídeos da GoPro
* [Impressão 3D](https://en.wikipedia.org/wiki/3D_printing): construiu a base de sustentação do protótipo
* [Servomotores](https://en.wikipedia.org/wiki/Servomotor): controle de posição das câmeras

Todo código gerado está disponível [nesse repositório do GitHub](https://github.com/matheusportela/maestro). Obviamente, ele não está muito legível pois tínhamos somente 33 FUCKING HORAS para terminar o projeto inteiro!

Melhor do que explicar em palavras, é ver como o protótipo funciona. Para tanto, assista ao nosso vídeo no YouTube.

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/bSnN2MHOCd4" frameborder="0" allowfullscreen></iframe></center>

É isso aí, pessoal. A diversão foi enorme e muita coisa boa foi criada em pouquíssimo tempo. Agradeço enormemente a todos os participantes, por terem gerado esse ambiente agradável e super amistoso, e pela equipe da Rede Globo, pela oportunidade incrível de criar novas tecnologias com todo suporte necessário disponível.

<center><figure><img src="/assets/images/equipe.jpg"/><figcaption>Participantes e organizadores do 1º Hackathon Globo</figcaption></figure></center>
