---
draft: false
title: Como organizar automaticamente seus arquivos - conforme seu formato de arquivo
seotitle: Como organizar automaticamente seus arquivos - conforme seu formato de arquivo
subtitle: 'Arrumando a bagunça'
description: >-
     Saiba manter seus arquivos, de determinado diretório, em pastas categorizadas conforme seu formato de arquivo. 
summary: >-
     Saiba manter seus arquivos, de determinado diretório, em pastas categorizadas conforme seu formato de arquivo.    
readingtime: '3'
slug: como-organizar-automaticamente-seus-arquivos-em-pastas-categorizadas-conforme-seu-formato-de-arquivo
date: 2020-01-22T15:25:12.051Z
#image
thumbnailImage: "https://lh3.googleusercontent.com/w6LCI9lnE9RltnhaQY4dVDGafq8_ZyI-Eh6c81G4WHmKTJv3iU-t7B2RSIX3_mv5Yw9re3Rf-IttysaJ2Q=w1000-no-tmp.jpg"
thumbnailImagePosition: left
coverImage: "https://lh3.googleusercontent.com/w6LCI9lnE9RltnhaQY4dVDGafq8_ZyI-Eh6c81G4WHmKTJv3iU-t7B2RSIX3_mv5Yw9re3Rf-IttysaJ2Q=w1000-no-tmp.jpg"
coverCaption: Foto Viktor Talashuk no Unsplash 
coverSize: partial
# somente se nao tiver thumb definido - ==> autoThumbnailImage: true
categories:
  - LinuxDescomplicado
tags:
  - python
  - pip
  - terminal
keywords:
  - linux
  - classifier
  - python
  - terminal
  - pip
---

Geralmente, existe uma pasta no seu sistema que, provavelmente, deve ser uma “bagunça”. Eu, particularmente, tenho a pasta “Downloads” como um depósito de arquivos. Assim, eu acabo me perdendo para encontrar alguma coisa. Caso você tenha o mesmo “problema”, existe uma ferramenta que promete te ajudar a manter seus arquivos, de determinado diretório, em pastas categorizadas conforme seu formato de arquivo. Conheça a ferramenta “Classifier”.

**Classifier** é um script simples, escrito em python, que promete organizar, instantaneamente, seus arquivos, com base na extensão do mesmo, em diferentes diretórios categorizados (**veja a ferramenta em ação**):

![](https://lh3.googleusercontent.com/xoFH3wCyZgq7WY8ZvNyOwbMHfjowgLEkvq60lOUeayfTDYPU_2tdlMZtWI1Hh_jaMiZjZJqecUWYqc_szQ=w1000-no-tmp.gif)

Por exemplo, ela criará, automaticamente, um diretório chamado Audio e moverá todos os arquivos “.mp3” para ele. Da mesma forma, move todos os arquivos zip/tar para uma pasta chamada “Archive”; filmes para uma pasta chamada “Videos” e assim por diante. Para fazer isso, simplesmente instale e execute esta ferramenta, que ela cuidará de tudo!

## INSTALAR A FERRAMENTA

Uma vez que é escrito em python, podemos facilmente instalá-la usando o pip – gerenciador de pacotes python.

[ADSENSE]

Arch Linux e derivados:

{{< highlight Bash shell scripts >}}
$ sudo pacman -S python-pip
{{< /highlight >}}

Debian, Ubuntu, Linux Mint:

{{< highlight Bash shell scripts >}}
sudo apt-get install python-pip
{{< /highlight >}}

RHEL, CentOS:

{{< highlight Bash shell scripts >}}
sudo yum install python-pip
{{< /highlight >}}

Fedora:

{{< highlight Bash shell scripts >}}
sudo dnf install python-pip
{{< /highlight >}}

openSUSE:

{{< highlight Bash shell scripts >}}
sudo zypper install python-pip
{{< /highlight >}}

Por fim, instale o Classifier:

{{< highlight Bash shell scripts >}}
sudo pip install classifier
{{< /highlight >}}

{{< highlight Bash shell scripts >}}
 Collecting classifier
 Downloading classifier-1.7.tar.gz
 Collecting arrow (from classifier)
 Downloading arrow-0.10.0.tar.gz (86kB)
 100% |████████████████████████████████| 92kB 250kB/s
 Requirement already satisfied: six>=1.10.0 in /usr/lib/python3.6/site-packages (from classifier)
 Collecting python-dateutil (from arrow->classifier)
 Downloading python_dateutil-2.6.0-py2.py3-none-any.whl (194kB)
 100% |████████████████████████████████| 194kB 389kB/s
 Installing collected packages: python-dateutil, arrow, classifier
 Running setup.py install for arrow ... done
 Running setup.py install for classifier ... done
 Successfully installed arrow-0.10.0 classifier-1.7 python-dateutil-2.6.0
{{< /highlight >}}

## ORGANIZAR AUTOMATICAMENTE SEUS ARQUIVOS

Depois de instalado a ferramenta, prossiga para o diretório onde estão os arquivos que deseja organizar. Depois, execute o comando ‘classifier’ para organizá-los automaticamente e movê-los para pastas categorizadas conforme a sua extensão de arquivo:

{{< highlight Bash shell scripts >}}
cd /home/ricardo/Download/
classifier

Scanning Files
Done!
{{< /highlight >}}

Pronto!! Veja seus arquivos organizados em pastas categorizadas!

Caso queira mais filtros, use um desses:

#### 1 – Classificar conforme data da criação do arquivo

{{< highlight Bash shell scripts >}}
classifier -dt
{{< /highlight >}}

#### 2 – Classificar conforme tipo do arquivo e mover para uma pasta específica

{{< highlight Bash shell scripts >}}
classifier -st .png -sf “Minhas Imagens”
{{< /highlight >}}

Para mais informações, execute:

{{< highlight Bash shell scripts >}}
classifier -h
{{< /highlight >}}

Útil para você?! Para mim, foi :)

## MAIS INFORMAÇÕES

* [Site Oficial](http://bhrigu.me/classifier/)
* [GitHub Oficial](https://github.com/bhrigu123/classifier)

***

Via | [Ostechnix](https://www.ostechnix.com/automatically-organize-similar-type-files-specific-folders/)
