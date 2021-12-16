---
draft: false
date: 2021-12-16T09:23:45-03:00
title: "Como acessar um servidor remoto, via linha de comando, sem SSH?"
description: >-
  Mostro como, sem um cliente/servidor SSH, por quaisquer motivos, você pode acessar 
  remotamente um servidor Linux tendo a base do modelo TCP/IP sólida
summary: "a"
subtitle: "Gosta de um desafio, né?"
seotitle: "Como acessar um servidor remoto, via linha de comando, sem SSH?"
slug: ""
# assets/images/post folder
image: "images/post/2021-12-acessoremoto_semssh.jpeg"
# static/images folder
seoimage: ""
caption: '<a href="https://unsplash.com/photos/ljNJn0ommQ8" target=_blank">Photo by Stephen Leonardi</a>'
tags: ["linux", "redes"]
# seo meta
keywords: ["linux", "redes", "tcp", "ip", "tcp/ip"]
categories: ["Linux"]
externalLink: ""
series:
---

Opa, tudo na paz, humano? 👽

Ricardo, aqui

**Gosta de um desafio, né?**

Com ele quero te convencer do porquê você deve dominar a base!! No caso, na prática, os **fundamentos do modelo TCP/IP**

Se liga...

### Modelo TCP/IP na prática

Dado as 4 camadas do modelo:

- Física
- Internet
- Transporte
- Aplicação

Vou ficar com a **camada de transporte** para te apresentar um caso real de como ter esses fundamentos, em mãos, 
te auxiliam, por exemplo, no **processo de troubleshooting**

Para ficar claro, essa camada é responsável por controlar a comunicação "host-a-host"

***"Não entendi, Ricardo!!"***

Na prática, o uso de portas e sockets de conexões. 

Logo, qualquer ferramenta que controle o estado IP:PORTA tá no escopo dela!

Pegou a ideia?

### Mão na massa

> Essa dica é para fins didáticos

Aqui, vou te mostrar como, sem um cliente/servidor SSH, por quaisquer motivos, você poderá acessar remotamente um destino tendo a base sólida e a ferramenta correta nas mãos

**Primeiro**, instale a ferramenta nmap tanto no servidor como no cliente.

Feito isso, vamos usar o **projeto ncat**, mantido pelos criadores do nmap, e libere a porta 50000 no servidor 
(no caso, a que você tiver permissão para liberar)

{{< highlight bash "style=dracula" >}}
sudo apt install nmap
{{< /highlight >}}

[TREINAMENTO]

No servidor, execute:

{{< highlight bash "style=dracula" >}}
ncat -vlp 50000 -e /bin/bash
{{< /highlight >}}

Onde,

- -v = verbose
- -l = escuta de conexão 
- -p = abre porta
- -e = permite executar comando

No cliente, execute:

{{< highlight bash "style=dracula" >}}
ncat IP-SERVIDOR 50000
{{< /highlight >}}

---

### Considerações Finais

O ncat instalado no servidor é visto como uma falha de segurança, devido a possibilidade de exploração de Shell reverso. 

Por isso, meu foco foi apenas te mostrar que sabendo bem os fundamentos de redes, você aumenta suas chances de resolver um desafio dessa natureza.

----

**Curtiu?**

Comenta aqui em embaixo qual seria outra maneira para resolver esse mesmo desafio. Gostaria muito de trocar essa ideia contigo!

Simbora!!

Tenho uma SUPER AULA completa que mostra na prática os fundamentos de redes no Linux. Forma quase 2h de pura imersão nesse fundamento tão importante para que área técnica de TI
