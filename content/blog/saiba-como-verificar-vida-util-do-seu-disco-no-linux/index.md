---
draft: false
title: Veja como verificar a vida útil do seu disco usando Linux
#seotitle: Você já se preocupou em verificar a vida útil do seu HD ou SSH?
subtitle: Nada é pra sempre! Inclusive, seu disco
description: >-
     Prever quando um disco irá falhar totalmente é quase improvável, pois defeitos podem começar a aparecer por vários motivos; até mesmo pela própria utilização normal do dispositivo.
summary: >-
     Prever quando um disco irá falhar totalmente é quase improvável, pois defeitos podem começar a aparecer por vários motivos; até mesmo pela própria utilização normal do dispositivo.
slug: saiba-como-verificar-vida-util-do-seu-disco-no-linux
date: 2020-02-17T16:25:12.051Z
categories:
  - Linux
tags:
  - smartmontools
  - S.M.A.R.T
keywords:
  - hd
  - ssd
  - smartmontools
  - terminal
---

Todos sabem que os discos (HDD ou SSD) são equipamentos feitos de componentes, **suscetíveis a desgastes**
com o passar do tempo. Prever quando um disco irá falhar é quase impossível, pois **defeitos podem começar** a 
aparecer por vários motivos; até mesmo pela própria utilização normal do dispositivo. 

Portanto, para evitar os famosos 'badblocks' (por exemplo), setores defeituosos na superfície do disco, 
que dificultam a leitura/escrita de dados deixando o tempo de resposta do disco muito lento, 
**você precisa saber diagnosticar o estado atual** do disco; antes mesmo que ele comece a falhar! 

[ADSENSE]

Atualmente os discos modernos podem realocar ou marcar os badblocks automaticamente, 
através do **serviço de monitoramento** chamado [SMART](https://pt.wikipedia.org/wiki/S.M.A.R.T.). 
Isso é impercetivel ao sistema operacional e ao usuário, por se um tratamento na camada de hardware do disco sendo 
desnecessário o intervenção manual. Mas, é sempre válido conhecer e definir um controle para um melhor acompanhamento da "saúde" do disco.

É possível monitorar os erros de leitura do disco (mesmo antes dos badblocks começarem a aparecer) usando o SMART. 
No Linux, este recurso é disponibilizado através do “smartmontools“, um pacote disponível nos repositórios da maioria das distribuições .

#### SMARTMONTOOLS

Todos recursos da ferramenta podem ser acessadas usando o **utilitário smartctl**.

Para começarmos a diagnosticar o disco é preciso acessar o terminal e executar o comando abaixo – responsável por coletar as informações do drive do disco:

{{< highlight Bash shell scripts >}}
sudo smartctl -i /dev/sda

=== START OF INFORMATION SECTION ===
Model Family: Western Digital Scorpio Blue Serial ATA
Device Model: WDC WD3200BEVT-75ZCT2
Serial Number: WD-WXF0A99E0057
LU WWN Device Id: 5 0014ee 2ae210af4
Firmware Version: 11.01A11
User Capacity: 320.072.933.376 bytes [320 GB] Sector Size: 512 bytes logical/physical
Device is: In smartctl database [for details use: -P show] ATA Version is: 8
ATA Standard is: Exact ATA specification draft version not indicated
Local Time is: Tue Aug 13 23:42:23 2013 BRT
SMART support is: Available – device has SMART capability.
SMART support is: Enabled
{{< /highlight >}}

Caso esteja informando: **SMART support is: Disabled**. Basta executar o comando abaixo para ativar o SMART:

{{< highlight Bash shell scripts >}}
sudo smartctl -s on /dev/sda
{{< /highlight >}}

#### Diagnosticando seu disco

{{< alert success no-icon >}}
**FIQUE SABENDO**

Devido a grande procura sobre esse tema, resolvi criar um curso focado nos fundamentos de discos e partições no Linux.

Curtiu? [Eu quero o curso](https://www.udemy.com/course/fundamentos-linux-sistemas-de-arquivos-e-dispositivos/?referralCode=BE4C4F68EECD104189ED)
{{< /alert >}}

O smartmontools oferece diversos níveis de diagnósticos – **Rápido e Longo**. No nível mais rápido já é possível coletar muitas informações úteis sobre a vida útil do seu disco!

Em primeiro lugar, execute o comando abaixo; para um diagnóstico rápido que **leva cerca de 2 minutos**:

{{< highlight Bash shell scripts >}}
sudo smartctl -t short /dev/sda

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: “Execute SMART Short self-test routine immediately in off-line mode”.
Drive command “Execute SMART Short self-test routine immediately in off-line mode” successful. Testing has begun.
Please wait 2 minutes for test to complete.
{{< /highlight >}}

Logo em seguida, execute o comando abaixo para exibir **um relatório de todos os auto-testes realizados** e o status de cada um.

{{< highlight Bash shell scripts >}}
sudo smartctl -l selftest /dev/sda
{{< /highlight >}}

Num disco saudável, todos reportarão **"Completed without error"**. Contudo, **no meu caso obtive o seguinte** (caso real que aconteceu com um disco meu :( ):

{{< highlight Bash shell scripts >}}
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                 
# 1  Short offline       Completed: unknown failure   
# 2  Short offline       Completed: unknown failure   
# 3  Short offline       Completed: unknown failure   
# 4  Short offline       Completed: unknown failure   
# 5  Short offline       Completed: unknown failure   
# 6  Conveyance offline  Completed: unknown failure   
# 7  Conveyance offline  Completed: unknown failure   
# 8  Short offline       Completed: read failure       
# 9  Short offline       Completed: read failure       
#10  Short offline       Completed: read failure       
#11  Short offline       Completed without error     
#12  Short offline       Completed without error    
{{< /highlight >}}

Como pode reparar, foi listado alguns erros na **coluna STATUS**. Isto caracteriza problemas no disco analisado. Para adquirir informações mais consistentes sobre esta situação é preciso executar outro comando!

O uso do parâmetro “-H” (health) exibe um diagnóstico rápido e preciso:

{{< highlight Bash shell scripts >}}
sudo smartctl -H /dev/sda
{{< /highlight >}}

Com este comando, obtive a certeza que meu disco está com um erro iminente :( 

{{< highlight Bash shell scripts >}}
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
Failed Attributes:
ID# ATTRIBUTE_NAME            TYPE       UPDATED             WHEN_FAILED
  5 Reallocated_Sector_Ct         Pre-fail       Always                FAILING_NOW      
{{< /highlight >}}

#### ENTENDENDO O RELATÓRIO

[ADSENSE]

Como foi destacado, o resultado do diagnóstico foi **FAILED** e com uma solução prática: **SAVE ALL DATA** (salve todos os seus dados)! Num disco saudável, seria **PASSED** :)

Mas é importante salientar alguns tópicos. A coluna TYPE (como destacada) descreve o tipo de falha. Neste caso, um disco “FAILED” não é um local seguro para guardar seus dados, mas em muitos casos ainda pode funcionar por alguns meses. 

Portanto, os casos marcados como TYPE “Old_age” indicam sintomas de que o disco está no final de sua vida útil, mas não significam por sí só problemas iminentes. Os mais graves são os TYPE “Pre-Fail”, que indicam que o disco está no final de sua vida útil – o meu caso 🙁

Na coluna “WHEN_FAILED” (a mais importante), você vê o status FAILING_NOW. Num disco saudável, esta coluna fica limpa para todas as opções, indicando que o disco nunca apresentou os erros!


{{< alert warning no-icon >}}
**AVISO**

Embora, relativamente raro, em muitos casos, o drive pode, realmente, danificar em menos de 24 horas, depois de indicado o erro. 
Por isso, transfira todos os dados importante, imediatamente!!
{{< /alert >}}

