---
draft: false
title: Conheça algumas maneiras para restaurar seu sistema Linux em caso de falhas
seotitle: Falhou! E agora? - Conheça algumas maneiras para restaurar seu sistema Linux
subtitle: Falhou! E agora? Não se desespere :)
description: >-
  Restaurar um sistema Linux parece algo improvável, já que não é uma função padrão da maiorias das distros Linux. 
  Por isso, seguem algumas ferramentas e opções que usam snapshots que servem para restaurar seu sistema Linux em caso de falhas.
summary: >-
  Restaurar um sistema Linux parece algo improvável, já que não é uma função padrão da maiorias das distros Linux. 
  Por isso, seguem algumas ferramentas e opções que usam snapshots que servem para restaurar seu sistema Linux em caso de falhas.
readingtime: '10'
slug: conheca-algumas-maneiras-para-restaurar-seu-sistema-linux-em-caso-de-falhas
date: 2020-01-12T12:25:12.051Z
thumbnailImage: "https://lh3.googleusercontent.com/I1mRKE7Wu4CB6fGrLrdb6XjKnoARCRXM8JoDnOm4rWNgXqWgbBq9Hjm1GQIcvsF2hE_cBTPkzSqFKFnqZQ=w1000-no-tmp.jpg"
thumbnailImagePosition: left
coverImage: "https://lh3.googleusercontent.com/I1mRKE7Wu4CB6fGrLrdb6XjKnoARCRXM8JoDnOm4rWNgXqWgbBq9Hjm1GQIcvsF2hE_cBTPkzSqFKFnqZQ=w1000-no-tmp.jpg"
coverCaption: Foto de chuttersnap no Unsplash
coverSize: partial
# somente se nao tiver thumb definido - ==> autoThumbnailImage: true
categories:
  - LinuxDescomplicado
tags:
  - backup
  - snapshots
keywords:
  - backup
  - snapshots
  - falha
  - recuperação
  - linux
---

Quem nunca quis dá um CTRL+Z no momento em que fez ou aconteceu algo errado? Aquele **botão “desfazer”**, 
encontrado em diversos programas, resolveria muitas coisas caso tivesse disponível para **restaurar seu sistema Linux** 
em situações inesperadas. 

Sendo assim, conheça algumas maneiras para restaurar seu sistema Linux em caso de falhas, possivelmente, **reversíveis é claro**.

## Contextualizando

![](https://lh3.googleusercontent.com/D1e7JZOBJnf87a3jefobbVSLoYkFgovBoxd5qBtiy1jdAcx-eEWa0qz7U39lN9paNQ8OFe9bvryCkNKZiA=w1000-no-tmp.jpg)
  
Restaurar um sistema Linux parece algo improvável, já que não é uma função padrão da maiorias das distros Linux. O termo &#8220;Ponto de Restauração&#8221; soa bem familiar para usuários Windows. Essa funcionalidade garante uma restauração completa do sistema, tendo uma vez salvo o &#8220;ponto&#8221; anterior à falha.

Contudo, mesmo não tendo essa característica disponível por padrão, os sistemas Linux possuem diversas ferramentas que oferecem a funcionalidade da &#8220;Restauração do Sistema&#8221;. A maioria delas são baseadas no mesmo princípio da restauração do sistema no Windows. Elas criam _snapshots_ (estados instantâneos) de seu sistema em intervalos especificados e deixa você reverter para um estado salvo anteriormente.

## Snapshots ?!

Para muitos, o mais óbvio e claro seria fazer backup do sistema regularmente; e quando fosse preciso recuperá-lo, bastava recuperar o último backup funcional. Contudo, existem diferenças entre **modelos de backup** e **snpashots**.

Comumente, as rotinas de backup armazenam, em espaço secundário, pastas e volumes do sistema. Quando se decide fazer backup de todo o disco, o <a href="http://www.linuxdescomplicado.com.br/2012/10/3-ferramentas-open-source-para-voce.html" target="_blank">processo passar a ser clonagem de disco</a>; o que garantem uma imagem fidedigna do disco.

Por outro lado, _snapshots_ são **estados instantâneos** de um sistema de arquivos criado em pontos específicos no tempo que é guardado e mantido no mesmo dispositivo de armazenamento. Eles geralmente incluem todos os diretórios e arquivos de um sistema de arquivos, ou, no mínimo, os arquivos necessários para o sistema operacional funcionar corretamente.

![](https://lh3.googleusercontent.com/iISZpVI0NatC6EYUXibcCdUtLrapXDJYxX7M32KqaEYAy0CfaKujmDm28tpvn54nmdfQCpYGPm_B6SRc3Q=w1000-no-tmp.jpg)

Manter um _snapshot_ no mesmo sistema de arquivos do SO torna possível executar uma reversão mais rápida; e também economiza espaço em disco, pois desse modo cada novo _snapshot_ não tem que salvar todo o estado do sistema de arquivos. Em vez disso, os futuros _snapshots_ passam a funcionar como **_backups incrementais_**, porque passam a salvar somente as alterações que foram feitas desde o último _snapshot_. 

Assim, significa que cada _snapshot_ depende do anterior para restaurar completamente o sistema. Diferentemente de <a href="http://www.linuxdescomplicado.com.br/2012/10/3-ferramentas-open-source-para-voce.html" target="_blank">uma imagem de um disco completo</a> que é independente de outros backups, contudo economiza bem mais espaço e precisa ser salvo em outra mídia secundária.

Entretanto, o problema com os _snapshots_ é claro&#8230; por salvarem no mesmo espaço do SO, passam a ficar vulneráveis a falhas do disco &#8211; se o disco sofrer danos mecânicos, você provavelmente vai perder os _snapshots_, juntamente com todo o sistema de arquivos do sistema. Para evitar isso, é recomendado fazer um _snapshot_ logo em seguida que instalar e configurar a sua distribuição Linux pela primeira vez. Depois copiá-lo para um dispositivo de armazenamento secundário.

Assim, seguem algumas ferramentas e opções **que usam snapshots** que servem para restaurar seu sistema Linux em caso de falhas.

#### TimeShift

![](https://lh3.googleusercontent.com/SDK2YioMYHVv_lLynC-MFeK5hBtRSewu89HkGrAnyuruySLqMP_3ez2JRzCKYvRPX2ZGriYrwcU0MWcBuQ=w1000-no-tmp.jpg)

TimeShift possui uma interface gráfica simples. Também é possível usá-lo a partir do terminal. Por padrão, no momento da criação do snapshot,  ele não inclui arquivos pessoais de um usuário (o diretório /home). Contudo, você pode adicionar pastas personalizadas nos seus snapshots ;-). 

Ele permite tirar snapshots sempre que quiser ou automaticamente, mediante configuração. Você pode agendar horários, que variam de diários, semanais e mensais; e configurar quantas vezes o TimeShift deve removê-los. Há uma opção especial chamada **Boot Snapshots** que cria um novo snapshot após cada reinicialização.

Para restaurar um snapshot você deve selecionar um &#8216;ponto&#8217; específico e escolher o local para o qual ele deve ser restaurado. O TimeShift oferece a opção de restaurar snapshots para dispositivos externos. Além disso, existem um recurso de &#8220;Clonagem&#8221; que permite copiar diretamente o estado atual do sistema para outro dispositivo &#8211;  útil para a migração para um novo computador, sem ter que configurar tudo do zero.

Para instalar em distros Ubuntu e derivadas:

<div class="terminal-widget">
$ sudo apt-add-repository ppa:teejee2008/ppa
$ sudo apt-get update
$ sudo apt-get install timeshift
</div>

#### Back In Time

![](https://lh3.googleusercontent.com/_20zVjNTasE4kK8zLwcIhdU-nZrzUDa9OZDclQliknEj0Q6j30f6fxjeDFLIQphYnUL6uO2n0emGLyWMcg=w1000-no-tmp.jpg)

**Back In Time** é amigável o suficiente para atrair iniciantes no Linux. Enquanto isso, a aba de Configurações oferece um controle refinado. A interface funciona como um gerenciador de arquivos regular, e você pode visualizar todos os seus snapshots, procurar arquivos em cada um deles, e restaurar arquivos e pastas selecionadas. 

O **Back In Time** cria snapshots que podem incluir pastas de sua escolha. Seus snapshots podem ser criptografadas e armazenadas em um dispositivo de rede, um disco externo, ou seu sistema de arquivos local. Ele atualiza somente os arquivos que foram alterados. Além disso, os snapshots podem ser agendadas (diário, semanal, mensal, várias vezes por dia ou somente após a reinicialização) ou você pode criá-los manualmente. 

Para instalar em distros Ubuntu e derivadas:

<div class="terminal-widget">
  $ sudo add-apt-repository ppa:bit-team/stable<br /> $ sudo apt-get update<br /> $ sudo apt-get install backintime-qt4
</div>

Caso a sua distro não ofereça o programa no repositório oficial, baixe o source <a href="https://github.com/bit-team/backintime/releases/tag/v1.1.12" target="_blank">aqui</a>.

#### SystemBack

![](https://lh3.googleusercontent.com/llvo2h8jiRHHqM7XcwRmOedpKrFLFE2HgEDDgA_qmFPdb3097fLUxql6t0R_yKnIwZ-CveCcZ1wvzIR8_w=w1000-no-tmp.jpg)

O Systemback é software de Backup. Ele se mostra como uma das melhores ferramentas para este nicho, por ser simples e fácil de usar, com diversos recursos.
  
Com ele você pode:

* Copiar o seu sistema completamente;
  
* Criar pontos de restauração; semelhante ao que acontece com a restauração do sistema do Windows;
  
* Criar sua própria distro LIVE, criando uma ISO inicializável

Para fazer a instalação nos sistemas Ubuntu e derivados &#8211; somente neles :(, execute os seguintes comandos (instalação via PPA):

<div class="terminal-widget">
  $ sudo apt-add-repository ppa:nemh/systemback -y<br /> $ sudo apt-get update<br /> $ sudo apt-get install systemback -y
</div>

Para mais informações de como usar essa ferramenta, <a href="http://www.linuxdescomplicado.com.br/2013/10/saiba-como-criar-um-ponto-de.html" target="_blank">segue tutorial completo</a>.

#### Snapper

![](https://lh3.googleusercontent.com/ebZXT_FVKMdBbO8USA0xsZm8GpV2Pv3asSIp9jQ7cTkFzaN2oYnCTH4VuvTRNXIUabGcI5GfD-Tq62L3nw=w1000-no-tmp.jpg)

Snapper está intimamente ligado ao <a href="http://www.linuxdescomplicado.com.br/category/distribuicoes/opensuse" target="_blank">openSUSE</a>, onde foi introduzido na versão 12.1. É possível instalá-lo em outras distribuições, mas não é garantido que funcione. A maneira mais fácil de configurar Snapper é instalar o openSUSE em uma partição Btrfs; nesse caso, Snapper é instalado e configurado automaticamente. Você pode usar o Snapper pela linha de comando ou através do YaST; e também há uma alternativa chamada **<a href="https://github.com/ricardomv/snapper-gui" target="_blank">snapper-GUI</a>**.

<div class='social-connect-widget'>
  <strong>MAIS INFORMAÇÕES</strong><br /> <a href="http://snapper.io/" target="_blank">Site Oficial</a>
</div>

## Soluções Avançadas

Talvez as aplicações mostradas até agora não sirvam por completo para você. Assim, existem soluções mais avançadas que podem atender diversas outras soluções.

#### Rsnapshot

[ADSENSE]

Ferramenta para sincronização de um sistema de arquivos local e remoto. É um utilitário de backup instantâneo (snapshot) baseado no rsync. Ele torna-se mais fácil para realizar backup instantâneos periódicos de máquinas locais e máquinas remotas através de SSH. A ferramenta faz uso extensivo de hard-links, sempre que possível, para reduzir significativamente o espaço em disco usado para armazenar os backups.

<div class="social-connect-widget">
  <strong>MAIS INFORMAÇÕES</strong><br /> <a href="http://rsnapshot.org/" target="_blank">Site Oficial</a>
</div>

#### Obnam

[ADSENSE]

Obnam é um programa de backup seguro e fácil de usar. Os backups podem ser armazenados em discos rígidos locais ou remotos, através do protocolo SFTP. Entre algumas características, destaco: suporte à snapshots (backups instantâneos), Deduplicação de dados e backups criptografados, usando o GnuPG .

<div class="social-connect-widget">
  <strong>MAIS INFORMAÇÕES</strong><br /> <a href="http://obnam.org/" target="_blank">Site Oficial</a><br /> <a href="http://linuxpitstop.com/install-obnam-on-ubuntu-15-04-and-centos-7/" target="_blank">Install Obnam on Ubuntu 15.04 and CentOS 7 – A simple, Secure Backup Utility</a>
</div>

#### LVM Snapshots

![](https://lh3.googleusercontent.com/QCUALtIoyKpWd-KuysYu9_yG17sY9LdZakLhdrqd-HWBwnlDk0D1uLzR-5zf5fcc6Rk9rjeieIE5ymGvTg=w1000-no-tmp.jpg)

LVM (Logical Volume Manager) é um método para alocar espaço do disco rígido, em volumes lógicos, que podem ser facilmente redimensionados; diferentemente das partições salvas nas tabelas de partições. Uma das grandes vantagens do uso do LVM é poder criar uma camada lógica sobre um disco rígido ou conjunto de discos e ter condições de de criar, excluir, redimensionar e expandir partições no disco sem precisar desligar o computador ou mover dados.

Quando se trata de preservar dados preciosos, é sempre uma boa ideia para pensar sobre isso com antecedência. Assim, vale a pena considerar o uso de LVM como uma maneira de organizar seus discos rígidos. Embora não seja exatamente um aplicativo, a implementação LVM vem com um recurso snapshot embutido no kernel do Linux. Você pode montar os snapshots e navegar neles como qualquer outro disco ou partição. Além disso, mesclar vários snapshots e restaurá-los para resolver problemas do sistema. 

