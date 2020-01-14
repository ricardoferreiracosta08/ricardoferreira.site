---
draft: false
title: >-
  7 comandos Linux que estão "obsoletos" há anos e, provavelmente, você ainda os
  usa
seotitle: 7 comandos Linux que estão "obsoletos" há anos e, provavelmente, você ainda os usa
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
#image
thumbnailImage: "https://lh3.googleusercontent.com/ViIQZq1KMDmB4IJDPmNkJmXyxnZsl4I510Zjt371_6kURG2W5zFLR5aR1FrGvQjeDldPk6oLVHy9ThUG4rUdodsuLVcCUsre0Je5E5Ow2W_yH54GhMSgZqLdOSjWmURTrTx676-zDk57F-WG0Ethfa7ruaXwjSx5kNe3HspfK2_Fu94j_khhYEz_Ms38t4wWKQAvaxmz2ltuRX50DtZvbAVxZCl5UAd4bXbqwbcRxcwRAJTYzSjQsv1GLSXx2wK40ucDzWDBHCcqpbvsgxyfbjJ2Tc7H3JQFwKZOfa1QXVZe8cDpuwbgtBcDaEjxTWV51jSymuoOZO4YT7al3PB2srI2JOlW84Wft61J9PRgvOwvgYm7xNhTvNBCNyDuytcmr2JaZ13lvmga6vAizl2Q2iqKnZsY0W7j3mf71b1Jao2aZqRvo5CiMrFFF9GFUKbneDgKPjiwiWW8fTlmbZJkAnybiWXs1mcDG53_Jo-8cH9ddimMMpKztWWVITsMzFqrB4L2_CJUO-_tZQ1ZQMN8TBHqPdUVS95URFHMRWSecfhMe_6g4eI_W2jI0R-1IQiVCnj_UPbDs8EUTFhhA31yb-iIyXwaSGtNUEpolVWF9hoFrJT7JGL3GfIwLJFYyhUlchBCaSypHZ8e0jhsrXnQJWzE59dbq7JSN4660o49u8cgjA73foYj7DM=w1200-h800-no"
thumbnailImagePosition: left
coverImage: "https://lh3.googleusercontent.com/VcVAr5l1K8DkLahiBQp_hxejnupdP72xwXGqioBk6Q7rcXFLpya217YquXV6lCEPG_EmGntT5ELNVKjXkHeOk5DO9-wWVqwkfOHwDIGy23a-8ilffV1xLKNIl2YEY828OBYYVpjeivCne7AbRJuFePvl9FGG65G52jxMw_qwOwm5Yi0QV8BD2arSeO3BZyCAHF5tQoEv3-pThLp-fYJf4EVe0JbO-5WX31VaWGKvaGSBls64Dn5nTKQjcwOd6_upj9VYx2wFGakr7wi-6Au0fz72VNUINvWqCSNfdA-uK8ApBP_32qjNJ6pq--EQh_xluF5zci0zFVpGOLytFeq63A9Rd3bJPuXmB77Fhou4dYGZHyaqVLlLCTx3sxUkfWkquwvihuwQGsg4PUNeaFzOIZfDB8_YNenrd5YTDwxxXQI03CiGr2VQwKC7hTZxGByGLnWnQawQmkYSUHIvdmrffUBbvebdyCCEsOZm7TtWA9cDGdY9TO8ZFvVRK8yzOyg9C2vhN7mLWQBvMoz1BwmfjlR6hFkQuwrUqsxWVJ3059-p6wubaMPeN4A72ZRHRIJKXSQeoMQnPJC2ktS-qH1sVprtJri2CehCRwmhSccgsfuIJWk6HPfmBk0vYh2I_DBRJRnTZ0sKl0Z4ENRzkq_DsYT5cLPmsIroBDYBaNuou89uaxlTzxXuBRg=w1420-h949-no"
coverCaption: Foto de Pixabay no Pexels    
coverSize: partial
# somente se nao tiver thumb definido - ==> autoThumbnailImage: true
categories:
  - LinuxDescomplicado
tags:
  - net-tools
  - ifconfig
  - iproute2
  - ip
  - terminal
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
