--- 
draft: false
date: 2021-12-03T10:41:25-03:00
tags: ["vdi", "desktop"]
keywords: ["linux", "vdi", "infraestrutura", "opensource"]
categories: ["Infraestrutura"]
seotitle: ""
title: "Virtualização de Desktop usando Infraestrutura Open Source"
subtitle: "Gerenciamento centralizado"
description: "Solução VDI open source que permite gerenciamento centralizado de desktops virtuais"
summary: ""
slug: "virtualizacao-de-desktop-vdi-infraestrutura-open-source/"
image: "images/post/2021_12_virtualizacao.jpg"
seoimage: "images/post/2021_12_virtualizacao.jpg"
caption: "<a href=\"https://unsplash.com/photos/uyfohHiTxho\" target=\"_blank\">Photo by ThisisEngineering RAEng</a>"
---

Hoje, vou trazer uma solução interessante para o negócio que permite o gerenciamento centralizado de desktops virtuais, facilidade de acesso, flexibilidade, maior segurança e mobilidade do usuário

<!--![Alt Text](https://i.imgur.com/g8FvFxB.gif)-->

Basicamente, o VDI (Infraestrutura de desktop virtual) faz uso de máquinas virtuais para fornecer e gerenciar Desktops Virtuais

Em resumo, é uma tecnologia que hospeda os sistemas numa infra central e os disponibiliza acesso desktop para os usuários

[TREINAMENTO]

Com 3 elementos base em sua estrutura:
- Virtualização + NAS
- Broker
- Terminais de acesso

O funcionamento é +/- esse:

1. o hypervisor segmenta desktops em máquinas virtuais. Cada desktop virtual inclui uma imagem do sistema operacional
2. Os usuários se conectam às instâncias de desktop por meio de um intermediário de conexão (broker), que é um gateway com base em software que atua como intermediário entre o usuário e o servidor. Ele encontra um desktop virtual dentro do pool de recursos para cada cliente se conectar após seu acesso bem-sucedido
3. os usuários podem acessar esses desktops virtuais em qualquer dispositivo ou local através de softwares de acesso remoto. Todo o processamento é feito no servidor central. Fortalece o conceito de BYOD - "traga você mesmo seu dispositivo"

As vantagens desse modelo são enormes. Podendo ser on-premise (HCI e cloud privada) ou em serviços DaaS (Desktop as a Service) em cloud pública

Por fim, como solução Full-Stack open source, em infra local, trago a **FlexVDI**

E como opções para cada pilar do VDI, deixo:

- **Virtualização:** Proxmox
- **NAS:** TrueNAS
- **Broker:** Ravada
- **ThinClient:** Remmina

E aí? Curtiu?

Simbora!!

***#tecnologia #opensource***

### Referências
- **Proxmox**: [https://www.proxmox.com/en/](https://www.proxmox.com/en/)
- **TrueNAS** [https://www.truenas.com/](https://www.truenas.com/)
- **Ravada** [https://ravada.upc.edu/](https://ravada.upc.edu/)
- **Remmina** [https://remmina.org/](https://remmina.org/)
- **FlexVID** [https://flexvdi.com/en/index](https://flexvdi.com/en/index)
