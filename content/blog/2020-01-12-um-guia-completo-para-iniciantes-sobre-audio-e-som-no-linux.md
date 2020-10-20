---
draft: false
title: Guia completo para iniciantes sobre áudio e som no Linux
seotitle: Tudo que precisa saber para entender sobre áudio e som no Linux
subtitle: Das vibrações do som a geração do áudio
description: >-
  No Linux há muitos programas que podem ajudar nas tarefas mais profissionais. Mas, é importante entender como funciona o áudio e som no Linux.
summary: >-
  No Linux há muitos programas que podem ajudar nas tarefas mais profissionais. Mas, é importante entender como funciona o áudio e som no Linux.
readingtime: '10'
slug: um-guia-completo-para-iniciantes-sobre-audio-e-som-no-linux
date: 2020-01-12T17:25:12.051Z
thumbnailImage: "https://lh3.googleusercontent.com/UQdl1iKRkDN9KwXAOTVMXIxLp2fijlaXqJ5GpBCnnwY1Erct76t3lcO98HPxCegXLAhJ2PkjhgwxVbl7mA=w1000-no-tmp.jpg"
thumbnailImagePosition: left
coverImage: "https://lh3.googleusercontent.com/UQdl1iKRkDN9KwXAOTVMXIxLp2fijlaXqJ5GpBCnnwY1Erct76t3lcO98HPxCegXLAhJ2PkjhgwxVbl7mA=w1000-no-tmp.jpg"
coverCaption: Foto de bruce mars no Pexels
coverSize: partial
# somente se nao tiver thumb definido - ==> autoThumbnailImage: true
categories:
  - Linux
tags:
  - som
  - alsa
  - pulseaudio
  - iniciante
keywords:
  - som
  - audio
  - linux
---

Quando se pensa em áudio e som no Linux vem logo a mente ferramentas voltadas para **produção musical** ou profissional da área. 

No Linux **há muitos programas** que podem ajudar nas tarefas mais profissionais. Mas, o foco agora é para todos os usuários que queiram entender como funciona o áudio e som no Linux. 

## Do começo

Primeiramente, áudio e som são coisas distintas. Conforme [Dicionário Informal](https://www.dicionarioinformal.com.br/diferenca-entre/%C3%A1udio/som/), áudio se refere a &#8220;transmissão ou reprodução eletrônica de um som&#8221;. Por outro lado, o som é &#8220;qualquer variação de pressão (no ar, na água&#8230;) que o ouvido humano possa captar&#8221;.

#### Como e o que eu posso ouvir?

Você pode se lembrar da escola que **o som são ondas que viajam pelo ar**. Vibrações de qualquer tipo fazem com que as moléculas do ar se movam. Quando essa forma de onda encontra seus ouvidos, ela faz com que os pelos do ouvido não se movam. Cabelos diferentes são suscetíveis a **frequências diferentes**, e os sinais enviados por esses cabelos são transformados em sons que você ouve em seu cérebro.

A **intensidade do som** vem da sua frequência, quanto mais curtas forem as ondas em uma forma de onda, maior será o som. O **volume do som** vem de quão altas as ondas são. A **audição humana** fica em um intervalo entre 20 Hz e 20.000 Hz, embora varie por pessoa. Para nós, as ondas abaixo de 20 Hz são chamadas de &#8220;infra-som&#8221; e as ondas acima de 20kHz são chamadas de &#8220;ultrassom&#8221;. Praticamente nenhum humano pode **ouvir além do ultrassom** &#8211; normalmente, sua audição limitara-se em 16kHz.

Para **entender tudo isso**, confira este [gerador de tom](https://www.szynalski.com/tone-generator), onde você pode experimentar diversas frequências e sons diferentes. 

***
> **VOCÊ SABIA?**
>
> A audição humana é bem limitada. Estamos entre as menores faixas de freqüência audíveis por seres vivos. 
> Por exemplo, um <strong>gato pode ouvir até 40kHz</strong> e os <strong>golfinhos podem ouvir até ouvir até 160kHz</strong>!!
> 
***

#### Como meu computador gera som?

Para ouvir o som, você provavelmente usará **fones de ouvido ou alto-falantes**. Dentro deles há cones que são acionados por um eletroímã, fazendo com que eles vibrem em frequências muito precisas. Isso é, basicamente, **como o som é reproduzido**. Embora os fones de ouvido modernos certamente sejam bastante complexos.

[ADSENSE]

Para acionar esse ímã, uma fonte de áudio enviará um sinal analógico (uma forma de onda) por um fio ao driver, fazendo com que ele se mova na frequência dessa forma de onda. Isto é, basicamente, **como funciona a reprodução de áudio** &#8211; e não vamos nos aprofundar muito mais do que isso.

**Computadores são digitais** &#8211; o que significa que eles não lidam com dados analógico; processadores entendem LIGADO e DESLIGADO; eles não entendem 38.689138% LIGADO e 78.21156% DESLIGADO. Ao **converter um sinal analógico** (como o som) em um digital, utilizamos um **[formato chamado PCM](https://pt.wikipedia.org/wiki/Modula%C3%A7%C3%A3o_por_c%C3%B3digo_de_pulsos)**. Para um PCM ser transformado em um sinal analógico, você **precisa de um DAC** &#8211; ou, literalmente, **uma placa de som**. DAC significa &#8216;Digital to Analog Converter&#8217;, ou algumas pessoas o chamam de &#8220;Digital Audio Converter / Chip&#8221;.

PCM significa **Pulse-code Modulation**, que é uma maneira de **representar sinais analógicos amostrados em um formato digital**. Imagine pegar uma amostra de uma forma de onda em intervalos regulares e armazenar o valor e, em seguida, arredondar esse valor para um &#8216;passo&#8217; mais próximo. Isso é PCM. A **precisão do PCM** vem de dois elementos, que não serão escopos do texto, mas que poderão ser lidos mais detalhadamentes [AQUI](https://www.reddit.com/r/linux/comments/coi4dt/a_complete_guide_of_and_debunking_of_audio_on): taxa de amostragem (sampling rate) e profundidade de bits (bit depth).

&#8211; **taxa de amostragem** é expressa em Hz e é com que frequência uma amostra de uma forma de onda é capturada;
  
&#8211; **profundidade de bits** é a informação armazenada em cada amostra;
  
&#8211; **canais** decidem quantas saídas simultâneas o PCM pode dirigir separadamente. Já que temos 2 ouvidos, você precisa de pelo menos dois canais 🙂

Como resultado&#8230; a **reprodução de áudio padrão** para usuários e profissionais é de 48kHz, 16 bits, 2 canais PCM. Isso é mais do que suficiente para representar totalmente o alcance total da audição humana.

## Áudio e som no Linux

Então, agora que sabemos como o PCM funciona, **como áudio e som no Linux funcionam?** Alguns componentes importantes entram em jogo aqui, e precisaremos discutir cada um deles com algum detalhe.

#### ALSA

ALSA é a **interface para o driver** de som do kernel. A **ALSA pode receber um sinal PCM** e enviá-lo ao seu hardware conversando com o driver. Algo importante a saber sobre a maioria das placas de sons é que eles só podem receber **um sinal de cada vez**, na verdade. Isso significa que apenas um único aplicativo pode enviar o som para o ALSA de uma só vez. Há muito tempo, em um tempo mais obscuro, você não podia assistir a um filme enquanto ouvia música :/

Este problema foi resolvido há muito tempo com o uso de **alsalib**, mas fazer mixagem em um nível de biblioteca não é uma solução muito boa para o problema. Isso deu origem a servidores de som, dos quais muitos já existiram. Antes do PulseAudio, o **esound** era muito popular, mas tinha muitos problemas, eventualmente foi **sucedido pelo PulseAudio**.

#### PulseAudio

Quando você pensa em áudio no Linux, o **PulseAudio** está provavelmente entre as primeiras coisas que você pensa. O PulseAudio NÃO é um driver nem fala com seus drivers. Na verdade, o PulseAudio **só faz duas coisas** que discutiremos em detalhes, posteriormente. O **PulseAudio fala com a ALSA**, assumindo o controle de seu único fluxo de áudio, e permite que **outros aplicativos conversem com o PulseAudio**. O **Pulse é um &#8216;multiplexador de áudio&#8217;**, transformando vários sinais em um através de um processo que é chamado de **mixagem**. A mixagem é um assunto incrivelmente complicado que não vamos falar aqui 🙂

[ADSENSE]

Essas **duas coisas permitem** que você jogue um jogo, ouça música e assista ao YouTube, além de notificações para produzir um som ao mesmo tempo. O PulseAudio é o elemento mais crítico da pilha de sons do Linux. O PulseAudio atualmente é um **software muito estável e sólido**. Se você tem problemas de áudio nos dias de hoje, geralmente é um problema no ALSA ou no seu driver.

## Outros servidores de som

O PulseAudio não é o único **servidor/daemon de som disponível para o Linux**, embora seja certamente o mais popular e provavelmente o padrão de qualquer distribuição que você esteja usando. O **PulseAudio tornou-se um padrão para o som do Linux** e tem, de longe, a melhor compatibilidade com a maioria dos aplicativos, mas isso não significa que não haja alternativas.

Então, listo algumas (existem outras alternativas):

#### JACK

O JACK Audio Connection Kit, um acrônimo recursivo como o GNU, é um servidor de som focado principalmente em baixa latência. Se você estiver fazendo um **trabalho de áudio profissional no Linux**, já estará familiarizado com o JACK. O desenvolvimento do JACK é muito focado em baixa latência, áudio em tempo real e é crítico para essas pessoas. O JACK está disponível na maioria das distros como uma alternativa, e você pode experimentar por si mesmo, se quiser; mas você pode achar que alguns aplicativos não funcionam bem com o JACK.

#### PipeWire

PipeWire é um projeto que está atualmente **em desenvolvimento**, procurando resolver os principais problemas que existem nos servidores de som atuais. O [PipeWire](https://pipewire.org/) não é apenas um servidor de som, mas também lida com a multiplexação de fontes de vídeo (como uma câmera). Especial atenção foi dada ao trabalho com aplicativos de área restrita (como <a href="https://www.linuxdescomplicado.com.br/2016/06/anuncio-do-flatpak-o-futuro-das-aplicacoes-linux-provalvelmente-o-concorrente-direto-ao-snap-da-canonical.html" rel="noopener noreferrer" target="_blank">Flatpaks</a>), que é uma área em que o PulseAudio está ausente. 

O PipeWire é um **projeto muito promissor** que pode muito bem ter sucesso com o PulseAudio no futuro e você deve esperar aparecer nos repositórios de distribuição muito em breve. Você pode testá-lo agora mesmo, embora não seja tão fácil começar como o JACK.

## Considerações

Aspectos mostrados foram base para um entendimento de como funcionam áudio e som no Linux. Para falarmos de **qualidade de áudio/som**, compre um boa placa de som externa. Uma boa placa fará uma melhoria significativa na sua experiência auditiva; e nada tem a ver com ALSA e PulseAudio 🙂

Seus fones de ouvido e amplificadores realmente fazem a maior diferença. Ter um bom par de fones de ouvido emparelhado com um bom amplificador de fone de ouvido dez vezes mais importante do que qualquer outro chip que você tenha no seu PC.

Por fim, **quebrando alguns mitos.** A qualidade de som do Linux **NÃO é pior** que o Windows. Eles são exatamente os mesmos, o Pulse não funciona tão diferente de como o Windows faz mixagens e reamostragens. E a qualidade de som do Linux **NÃO pode ser melhor** que o Windows. Eles são exatamente os mesmos. Todas as melhorias na qualidade vêm do driver e da sua placa de som, não do servidor de som :/

Via | Excelente artigo do [usuário _Spell_](https://www.reddit.com/user/_Spell_/) publicado no [Reddit](https://www.reddit.com/r/linux/comments/coi4dt/a_complete_guide_of_and_debunking_of_audio_on/)
