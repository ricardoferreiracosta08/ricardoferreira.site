---
draft: false
title: >-
  7 comandos Linux que estão "obsoletos" há anos e, provavelmente, você ainda os
  usa
subtitle: 'ifconfig, netstat e outros'
description: >-
  Embora ainda funcionais, esses comandos são, realmente, considerados obsoletos
  e, portanto, devem ser renunciadas em favor de ferramentas mais "modernas".
summary: >-
  Embora ainda funcionais, esses comandos são, realmente, considerados obsoletos
  e, portanto, devem ser renunciadas em favor de ferramentas mais "modernas".
slug: >-
  ifconfig-e-outros-comandos-linux-de-rede-obsoletos-ha-anos-e-que-ja-possuem-sucessores
date: 2019-12-03T12:51:56.868Z
image: /images/pexels_photo_128428.jpg
categories:
  - LinuxDescomplicado
tags:
  - net-tools
  - ifconfig
  - iproute2
  - ip
keywords:
  - iproute
  - ifconfig
  - ip
  - net tools
  - linux
---
Os comandos arp, ifconfig, iptunnel, netstat, route, iwconfig e nameif foram (ainda são) essenciais para administrar configurações de rede no Linux, mas estão obsoletos há anos e, provavelmente, você ainda os usa; deixaram de ser mantidos e passaram ao status, de desenvolvimento, “deprecated” por várias distribuições Linux. 

Embora ainda funcionais, elas são, realmente, consideradas obsoletas e, portanto, devem ser renunciadas em favor de ferramentas mais "modernas".

## **Pacote net-tools**

Os comandos de rede Linux, em questão, **arp, ifconfig, iptunnel, netstat, route, iwconfig e nameif** fazem parte do **[pacote "net-tools"](https://wiki.linuxfoundation.org/networking/net-tools)**. Contudo, esse pacote não é mantido há anos (décadas), tornando as ferramentas presentes nele obsoletas. 

![network communication](../../../images/network_communicatio_Akldj.jpg) 

A funcionalidade fornecida por vários desses comandos foi "melhorada" no **[novo pacote "iproute2"](http://en.wikipedia.org/wiki/Iproute2)**, principalmente através do seu **novo comando ip**. O código do pacote "iproute2" está disponível no **[Kernel.org](https://www.kernel.org/pub/linux/utils/net/iproute2/)**. A documentação do "iproute2" está disponível na [**wiki Oficial do Linux Foundation**](http://www.linuxfoundation.org/collaborate/workgroups/networking/iproute2) e no **[PolicyRouting.org](http://www.policyrouting.org/iproute2-toc.html)**.

## **Obsoletos?**

Qualquer **pessoa que tenha administrado sistemas Linux** por qualquer período de tempo certamente **aprendeu a usar os utilitários de ferramentas de rede** para realizar suas tarefas. Se você está acostumado a usar comandos como ifconfig, arp e netstat para executar tarefas de rede, você **deve repensar seus hábitos**.

![time](../../../images/e8005d337be2fcd130d1_i8S4v.jpg) 

Para esses comandos, **[o status "deprecated" vem sendo anunciado há alguns anos](http://br-linux.org/2016/01/deprecated-ifconfig-route-e-outros-comandos-classicos-de-rede-no-linux-que-tem-sucessores-que-voce-precisa-conhecer.html)**, embora muita gente continue sem saber. Muito se deve a vários manuais e tutoriais que continuam se fixando na forma clássica e a **[desenvolvedores de ferramentas de rede que ainda usam esses utilitários](https://lwn.net/Articles/710533/)** :( 

Por enquanto, os usuários que estão acostumados a digitar comandos como estes, provavelmente, ainda estão seguros. Na pior das hipóteses, eles precisam instalar o pacote "net-tools", explicitamente, caso já esteja instalado na sua distribuição Linux (o **[Debian 9](https://www.linuxdescomplicado.com.br/2017/06/debian-9-stretch-atualizacao-de-uma-das-maiores-distribuicoes-linux-e-divulgada-confira-novidades.html)** parece não mais tê-lo instalado por _default_). Em resumo, o **status "deprecated**" representa que um pacote não está mais sendo mantido, mas ainda funciona, podendo deixar de funcionar caso os desenvolvedores das distribuições o decidam fazer. Portanto, é bom ter em mente os "novos" comandos de rede que devem ser usados em substituição aos "antigos".

## **O Sucessor**

O **[iproute2](https://wiki.linuxfoundation.org/networking/iproute2)** é uma coleção de utilitários para controle de redes TCP/IP e controle de rede no Linux. Atualmente, é mantida por **Stephen Hemminger**. O autor original é o **Alexey Kuznetsov**, conhecido pela implementação da QoS no kernel do Linux. A maioria dos manuais de configuração de rede ainda se refere ao ifconfig e route como as principais ferramentas de configuração de rede, mas o [**ifconfig é conhecido por se comportar de forma inadequada em ambientes de rede modernos**](https://wiki.linuxfoundation.org/networking/iproute2). Assim, eles são considerados obsoletos, **mas a maioria das distros ainda os inclui**. Sendo assim, segue lista com os comandos obsoletos e seus respectivos "sucessores" contidos no pacote **[iproute2](https://wiki.linuxfoundation.org/networking/iproute2)**:

|Obsoleto|Sucessor|
|--- |--- |
|arp|ip n (ip neighbor)|
|ifconfig|ip a (ip addr), ip link, ip -s (ip -stats)|
|iptunnel|ip tunnel|
|route|ip r (ip route)e|
|nameif|ip link, ifrename|
|iwconfig|iw|
|netstat|ss, ip route (for netstat-r), ip -s link (for netstat -i), ip maddr (for netstat-g)|
|mii-tool|ethtool|

**MAIS INFORMAÇÕES** 

* [Net-tools obsoleto - Anúncio Linux Foundation](http://www.linuxfoundation.org/collaborate/workgroups/networking/net-tools)
* [iproute2 - sucessor ao net-tools](https://wiki.linuxfoundation.org/networking/iproute2) [Moving on from net-tools - Artigo Lwn.net](https://lwn.net/Articles/710533/)

* * *

Via | [Blog Dougvitale](https://dougvitale.wordpress.com/2011/12/21/deprecated-linux-networking-commands-and-their-replacements/)
