---
draft: false
title: >-
  Saiba como compilar e instalar programas Linux distribuídos diretamente pelo
  código-fonte [tar.gz]
subtitle: './configure, make e make install'
description: "Hoje em dia, instalar programas no Linux se tornou a coisa mais simples de se fazer no sistema. Dependendo da distribuição Linux, você tem recursos complementares que facilitam ainda mais o processo. Contudo, em muitos momentos você se depara com programas\_disponibilizados\_diretamente pelo código-fonte."
summary: "Hoje em dia, instalar programas no Linux se tornou a coisa mais simples de se fazer no sistema. Dependendo da distribuição Linux, você tem recursos complementares que facilitam ainda mais o processo. Contudo, em muitos momentos você se depara com programas\_disponibilizados\_diretamente pelo código-fonte."
slug: >-
  saiba-como-compilar-e-instalar-programas-linux-distribuidos-diretamente-pelo-codigo-fonte-tar-gz
date: 2019-12-02T15:18:46.703Z
image: /images/pexels_photo_374563.jpg
categories:
  - LinuxDescomplicado
tags:
  - tar.gz
  - compilação
keywords:
  - linux
  - tar.gz
  - compilação
  - programas
  - instalação
  - configure
  - make
  - make install
---
Hoje em dia, instalar programas no Linux se tornou a **coisa mais simples** de se fazer no sistema. Dependendo da distribuição Linux, você tem recursos complementares que facilitam ainda mais o processo. **Gerenciadores de pacotes** e repositórios oficiais, mantidos pela comunidade mantenedora da distribuição, enriquecem o processo de instalação dos programas. 

Contudo, em muitos momentos você se depara com programas disponibilizados diretamente pelo código-fonte. Assim, cabe ao usuário ter conhecimento prévio para compilar e instalar programas Linux distribuídos diretamente pelo código-fonte, normalmente compactados **via tar.gz**.

## Contextualizando

As distribuições Linux, ao longo do tempo, vem melhorando e criando métodos para facilitar a instalação de pacotes no Linux. Gerenciadores de pacotes, bem como: **apt e yum**, são exemplos legados dessas mudanças. Atualmente, **existem projetos** que visam a **universalização do modo e distribuição de programas** para os sistemas Linux. 

Entre eles, destaco o [Snap](http://www.linuxdescomplicado.com.br/2016/06/pacotes-snap-do-ubuntu-podem-se-tornar-formato-universal-para-todas-as-distribuicoes-linux.html) e [Flatpak](http://www.linuxdescomplicado.com.br/2016/06/anuncio-do-flatpak-o-futuro-das-aplicacoes-linux-provalvelmente-o-concorrente-direto-ao-snap-da-canonical.html); Canonical e Red Hat como mantenedoras, respectivamente. Entretanto, vão aparecer situações onde você não terá nenhuma dessas opções disponíveis... pois alguns desenvolvedores de softwares **disponibilizam seus programas diretamente pelo código-fonte (source) -** que por sinal **era, nos primórdios, o único método utilizado** para instalação de programas no Linux (algumas distribuições ainda mantêm essa técnica com frequência).

Em resumo, você tem acesso a um arquivo compactado no **formato .tar.gz** (maioria das vezes), contendo o código-fonte do programa, e **a instalação consiste em compilar e instalar** os executáveis gerados na máquina. Mas por quê ainda se preocupar com isso se existem **pacotes pré-compilados para instalação**?!

**SAIBA MAIS** 
***
> Pacotes pré-compilados são pacotes já compilados e distribuídos num arquivo pronto, com dependências já configuradas, em um formato simples de instalar (.deb - Debian e .rpm - Red Hat, por exemplo).
***

Devido às **diferenças** que existem entre uma distribuição e outra um pacote do Fedora não funcionará no Debian, por exemplo. Assim, essa **técnica** garante suporte a todas as distribuições Linux, universalmente! Ou seja, baixando um programa distribuído a partir do código-fonte (source), **não será preciso** se ater a qual distro Linux você está usando; pois, verificada as dependências necessárias, será possível compilar e instalar o programa. Isso se deve ao fato de que essa maneira de distribuir os programas, diretamente pelo código-fonte (source), não é feita por **empacotamento pré-compilado** (pacote .deb ou .rpm, por exemplo). Assim, cabe ao usuário ter conhecimento prévio para compilar e instalar programas Linux distribuídos diretamente pelo código-fonte, normalmente **compactados via tar.gz**.

**SAIBA MAIS** 
***
> Compilar significa transformar o código-fonte, escrito pelo programador, nos arquivos binários que são executados pelo sistema.
***

Por outro lado, um problema, em compilar e instalar programas a partir dos fontes, é que o processo é demorado e, para muitos, nem sempre simples. É preciso ter instalado uma grande quantidade de compiladores e bibliotecas, necessários para compilar os mais diversos programas. E isso causa bastante dificuldade para os usuários, principalmente iniciantes.

## Em 4 passos...

Resumindo o processo de instalação de programas disponibilizados a partir do código-fonte, informo que o mesmo se dá em 4 passos: 1- Descompactar o arquivo tar.gz que **contém o código-fonte**; 2- Resolver **dependências necessárias** para a instalação correta do programa - cada programa possui suas próprias dependências, e isso torna processo demorado e um pouco mais complicado. Cada programa tem sua peculiaridade; 3- Compilar; 4- Instalar;

**DETALHES** 
***
> Neste tutorial usei como exemplo o programa **[Pidgin IM](https://www.pidgin.im/)** e o sistema **[OpenSUSE Tumbleweed](http://www.linuxdescomplicado.com.br/2016/05/por-que-resolvi-trocar-o-ubuntu-lts-pelo-opensuse-tumbleweed.html)**
***

#### 1- Baixar e descompactar o arquivo tar.gz

Primeiramente, faça o download do **arquivo pidgin-2.11.0.tar.gz** [AQUI](https://sourceforge.net/projects/pidgin/files/Pidgin/) [ **Versão 2.11.0** ] O arquivo baixado é um tarball, geralmente é identificado através do uso de duas extensões ".tar" e ".gz", combinadas para formar ".tar.gz". Uma extensão combinada simples, .tar.bz também é popular. Esse formato usa o **utilitário tar** para criar um único _**tarfile**_ com todo o conteúdo do diretório - o código-fonte do programa, no caso. Para descompactar o conteúdo do arquivo **arquivo pidgin-2.11.0.tar.gz**, você deve executar o comando:

{{< highlight Bash shell scripts >}}
tar -xzvf pidgin-2.11.0.tar.gz
{{< /highlight >}}

Entre no diretório descompactado:

{{< highlight Bash shell scripts >}}
cd pidgin-2.11.0
{{< /highlight >}}

O conteúdo do diretório **contém o código-fonte da aplicação** e o **arquivo Makefile**, entre outros arquivos. **Essa estrutura garante um programa distribuído a partir do código-fonte** (source) ;-) Por isso, **nem todo arquivo "tar.gz"** significará um programa distribuído dessa forma; poderá ser apenas um arquivo compactado.

**SAIBA MAIS** 
***
> O Makefile é um arquivo para configuração de compilação utilizado pelo programa make, cuja ideia é simplificar e agilizar a compilação de programas.
***

#### 2- Resolver dependências

Esta etapa pode ser considerada a mais "complexa" do processo, pois caso as dependências necessárias, da aplicação, não sejam atendidas o código-fonte não poderá ser compilado e instalado, futuramente. E cada aplicação possui um leque diferente de dependências. No caso do programa Pidgin **existem algumas dependências que precisam ser resolvidas** - ou seja pacotes que já precisam estar instalados no sistema, pois caso contrário dará erro no processo! Em distribuições derivadas do Debian, a principal dependência é pacote de compiladores que contém todas as ferramentas básicas para compilação de um programa. Muito conhecido, chamado de **build-essential**:

{{< highlight Bash shell scripts >}}
sudo apt-get install build-essential
{{< /highlight >}}

Como usei o OpenSUSE, o pacote equivalente é o **devel_basis**:

{{< highlight Bash shell scripts >}}
sudo zypper install -t pattern devel_basis
{{< /highlight >}}

Assim, depois de satisfazer as dependências do sistema, é preciso resolver as pendências da aplicação. Para isso, você DEVE executar o comando:

{{< highlight Bash shell scripts >}}
./configure
{{< /highlight >}}

Esse comando **verifica todas dependências que o programa precisa**, como se o pacote de compiladores está instalado; por exemplo. O prefixo ./ diz ao sistema Linux para **procurar o arquivo de configuração no diretório atual e executá-lo**. Assim, você precisa estar dentro do diretório do programa (**pidgin-2.11.0**) para poder executar esse comando:

{{< highlight Bash shell scripts >}}
[ .... ] 
checking for strdup... yes 
checking for strstr... yes 
checking for atexit... yes 
checking for setlocale... yes 
checking for getopt_long... yes 
checking for inet_aton... yes 
checking for __res_query in -lresolv... yes 
checking for gethostent in -lnsl... yes 
checking for socket... yes 
checking for getaddrinfo... yes 
checking for inet_ntop... yes 
checking for getifaddrs... yes 
checking for socklen_t... yes 
checking for struct sockaddr.sa_len... no checking whether IPV6_V6ONLY is declared... yes 
checking for special C compiler options needed for large files... no 
checking for _FILE_OFFSET_BITS value needed for large files... no 
checking for dlopen... no 
checking for dlopen in -ldl... yes 
checking for library containing ceil... -lm checking for fileno()... yes 
checking for the %z format string in strftime()... yes 
checking whether NLS is requested... yes 
checking for intltool-update... /usr/bin/intltool-update checking for intltool-merge... /usr/bin/intltool-merge checking for intltool-extract... /usr/bin/intltool-extract checking for xgettext... /usr/bin/xgettext checking for msgmerge... /usr/bin/msgmerge checking for msgfmt... /usr/bin/msgfmt 
[ .... ]
{{< /highlight >}}

Se tudo correr bem, **você não verá quaisquer erros**:

{{< highlight Bash shell scripts >}}
[ ... ] 
Build with Perl support....... : yes 
Build with Tcl support........ : yes 
Build with Tk support......... : yes 
Print debugging messages...... : no 
**Pidgin will be installed in /usr/local/bin. configure complete, now type 'make'**
{{< /highlight >}}

Caso apresente algum erro, basta examinar a saída do comando ./configure e instalar/configurar todas as dependências ausentes usando seu gerenciador de pacotes. Execute ./configure **quantos vezes for preciso até que você não veja mais erros** ;-) No meu caso (com o openSUSE Tumbleweed instalado), **tive alguns erros** que avisaram a ausência de alguns pacotes. Portanto, segue lista de todos os pacotes que foi precisa instalar no meu ambiente de testes:

**AVISO** 
***
> Cada sistema vai apresentar **resultados diferentes**. Pois, poderão surgir dependências que estarão resolvidas e outras não. Por isso, essa etapa requer mais atenção do usuário Linux.
***

{{< highlight Bash shell scripts >}}
sudo zypper install intltool glib2-devel gtk2-devel libXss1 libXss.so.1 libXss-devel libSM-devel meanwhile-devel libgnutls-devel tcl-devel tk-devel
{{< /highlight >}}

#### 3- Compilação

Depois de ter resolvido todas as dependências, você deve compilar o programa. Use o **comando make** para fazer isso:

{{< highlight Bash shell scripts >}}
make
{{< /highlight >}}

Este processo pode demorar alguns minutos, dependendo do programa. Certifique-se de que a saída não exibirá quaisquer erros antes de continuar para o próximo passo ;-)

#### 4- Instalação

Pronto... não tendo apresentado nenhum erro até agora, você precisa instalar o programa. Basta executar **sudo make install**. Este passo move todos os binários em seu local correto no seu sistema para que o programa fique pronto para usar:

{{< highlight Bash shell scripts >}}
sudo make install
{{< /highlight >}}

Programa instalado!!   Mas, se você desejar remover o programa, que acabou de instalar, basta entrar no diretório que você instalou o programa e executar os 2 comandos abaixo:

{{< highlight Bash shell scripts >}}
sudo make uninstall 
sudo make clean
{{< /highlight >}}

Por fim, informo que para instalar a maioria dos programas a partir do código-fonte (source), você passará pelas mesmas situações do exemplo. Contudo, com algumas diferenças das mostrados aqui. Por exemplo, você pode **precisar usar cmake em vez de make**. Por isso, sempre leia o arquivo "README" contido no diretório de cada programa!! Além dele, normalmente, existe o arquivo "Install" também ;-)

* * *

Via | [MakeTechEasier](https://www.maketecheasier.com/compile-linux-programs-source/)
