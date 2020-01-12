---
draft: false
title: Saiba como, facilmente, ocultar arquivos e pastas no Linux
seotitle: Como ocultar arquivos e pastas no Linux - sem programa, recurso extra ou dificuldade
subtitle: A coisa mais fácil que você fez ou vai fazer no Linux
description: >-
  Ocultar um arquivo e pastas no sistema de arquivos do Linux é algo tão simples que nem precisa instalar ou 
  configurar algo no sistema. Desde dos primórdios do sistema existe um recurso amplamente usado para ocultar arquivos e pastas no Linux. 
summary: >-
  Ocultar um arquivo e pastas no sistema de arquivos do Linux é algo tão simples que nem precisa instalar ou 
  configurar algo no sistema. Desde dos primórdios do sistema existe um recurso amplamente usado para ocultar arquivos e pastas no Linux. 
readingtime: '3'
slug: aplicacoes-cientificas-para-linux-eletronica-estatistica-fisica-e-mais
date: 2020-01-10T21:25:12.051Z
thumbnailImage: "https://lh3.googleusercontent.com/le-0dCFAYv0O5hoMLs7YkZy5YnzrLpcqM5exTxv-Ey9Hm3gj7V5iHsjupREv-NqHFn-lWTKIkHld_yWB4A=w1000-no-tmp.jpg"
thumbnailImagePosition: left
coverImage: "https://lh3.googleusercontent.com/le-0dCFAYv0O5hoMLs7YkZy5YnzrLpcqM5exTxv-Ey9Hm3gj7V5iHsjupREv-NqHFn-lWTKIkHld_yWB4A=w1000-no-tmp.jpg"
coverCaption: Foto de Aron Van de Pol no Pexels
coverSize: partial
# somente se nao tiver thumb definido - ==> autoThumbnailImage: true
categories:
  - LinuxDescomplicado
tags:
  - ocultar
  - arquivos
  - pastas
keywords:
  - ocultar
  - arquivos
  - pastas
  - linux
---

Independentemente do motivo, provavelmente, você já quis ocultar algum arquivo ou pasta em seu sistema Linux. Entre algumas maneiras para fazer isso, mostrarei o processo “menos complicado” para fazer isso; e de maneira rápida, simples e eficiente.

## Ocultar arquivos e pastas no Linux

**Ocultar um arquivo** e pastas no sistema de arquivos do Linux **é algo tão simples** que nem precisa instalar ou configurar algo no sistema. Desde dos primórdios do sistema existe um recurso amplamente usado para ocultar arquivos e pastas no Linux. O método consiste em renomear o arquivo ou pasta e colocar o caracter &#8220;.&#8221; (ponto) na frente dele.

Encontre um arquivo ou diretório que você deseja ocultar e selecione-o. Clique com o botão direito do mouse e selecione &#8220;Renomear&#8221;. Em seguida, coloque o caracter &#8220;.&#8221; (ponto) no início do arquivo:

![](https://lh3.googleusercontent.com/ZSoRS85pwabvFOpLqQVgvVMFBBqSI5Brzgo_qR5-Q1uU6iUEzv0TDEYgf9cKbNGbWrEM_lbVGTNgjexPSA=w1000-no-tmp.jpg)

Como a maioria dos gerenciadores de arquivos &#8220;suportam&#8221; esse método para ocultar arquivos, o arquivo ou diretório renomeado ficará &#8220;invisível&#8221;. Além disso, os arquivos (mesmo sem o &#8220;.&#8221; no início do nome deles) colocados em um diretório oculto (com o &#8220;.&#8221; no início do nome da pasta) também serão ocultos, por padrão 😉

![](https://lh3.googleusercontent.com/7KkS_URSjcBda522IHDzZv7HRxSCbBaUUBRaBsx-nOZsJerER9L-Lr2gSqWvPt6Kf7WWtuuyW-od0HU54w=w1000-no-tmp.jpg)

O processo para **visualizar** **esse arquivo ou pasta oculto** consiste em, no modo gráfico, ir nas opções de visualizações do gerenciador de arquivos do sistema e escolher &#8220;mostrar arquivos ocultos&#8221;. Na maioria dos gerenciadores de arquivos, as teclas de atalho &#8220;CTRL+H&#8221; funcionam normalmente 😉 Já no modo de linha de comandos, basta ir ao diretório que contém os arquivos ou pastas ocultos e executar:

{{< highlight Bash shell scripts >}}
$ ls -lha
{{< /highlight >}}
Mas, caso queira tornar o arquivo ou pasta novamente “visível” basta remover o “.” (ponto) no início do nome de cada um deles 😉

## IMPORTANTE

--- 
> O processo mostrado apenas garante a ocultação do arquivo/pasta. Não garante a segurança do mesmo; já que qualquer com o conhecimento suficiente conseguirá visualizar os arquivos “escondidos” e reverter o processo!

> Caso esteja procurando algo seguro, você precisará adotar recursos de criptografia de dados ou uso da esteganografia – “uso de técnicas para ocultar a existência de uma mensagem dentro de outra, uma forma de segurança por obscurantismo”.

---

## Por que esse recurso é possível?!

Para muitos isso **pode ser uma falha ou vulnerabilidade do sistema**. De [acordo com o Linux Audit](https://linux-audit.com/linux-history-how-dot-files-became-hidden-files/), tudo “começou” há muitos anos, quando os primeiros sistemas de arquivos foram criados no UNIX.

Para permitir a navegação fácil, um único arquivo com um ponto (.) foi adicionado em cada diretório. Em segundo lugar um arquivo de ponto duplo (..) foi adicionado para mover facilmente para cima na estrutura de diretório. Como esses arquivos não tinham dados reais neles, um “recurso” rápido foi adicionado ao binário “ls” – comando responsável por listar conteúdo de diretórios nos sistemas Linux.

[ADSENSE]

O recurso, adicionado ao **binário ls**, envolveu **a verificação do primeiro caractere**. Se isso fosse um ponto, ele deve ser ignorado. E funcionou muito bem.

Sendo assim, **o recurso foi criado para outros propósitos**, mas até hoje muitos (principalmente, os programadores) usam para ocultar arquivos e/ou pastas no sistema. Mas, independentemente de tudo isso **o recurso está disponível** e uma **“mão na roda”** para quem deseja, facilmente, **ocultar arquivos e pastas no Linux** \o/
