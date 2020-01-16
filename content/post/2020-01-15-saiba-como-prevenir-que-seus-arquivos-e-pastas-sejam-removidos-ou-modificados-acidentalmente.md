---
draft: false
title: Como prevenir que seus arquivos sejam removidos, acidentalmente
seotitle: Já pensou remover um arquivo acidentalmente? Veja como prevenir que isso ocorra
subtitle: Já pensou remover um arquivo sem intenção? 
description: >-
  Caso você queira prevenir que seus arquivos e pastas sejam removidos ou modificados acidentalmente, 
  basta você usar ferramentas definidas, por padrão, nos sistemas Linux.
summary: >-
  Caso você queira prevenir que seus arquivos e pastas sejam removidos ou modificados acidentalmente, 
  basta você usar ferramentas definidas, por padrão, nos sistemas Linux.
slug: saiba-como-prevenir-que-seus-arquivos-e-pastas-sejam-removidos-ou-modificados-acidentalmente
date: 2020-01-15T22:35:51.240Z
#image
thumbnailImage: "https://lh3.googleusercontent.com/u1JXqvNI1dkLnSrJaXYcDe7-UwF9gxZirkc4Ydj_N5wJBvgRE4Zfyp-48Nt6RH_qcWzbMTUN6nxK5cx30Q=w1000-no-tmp.jpg"
thumbnailImagePosition: left
coverImage: "https://lh3.googleusercontent.com/u1JXqvNI1dkLnSrJaXYcDe7-UwF9gxZirkc4Ydj_N5wJBvgRE4Zfyp-48Nt6RH_qcWzbMTUN6nxK5cx30Q=w1000-no-tmp.jpg"
coverCaption: ""
coverSize: partial
# somente se nao tiver thumb definido - ==> autoThumbnailImage: true
categories:
  - LinuxDescomplicado
tags:
  - chattr
  - terminal
keywords:
  - chattr
  - terminal
  - linux
---

As principais técnicas de proteção a leitura e escrita, e até a remoção, de seus arquivos no sistema Linux podem ser feitas sem a instalação de softwares adicionais. Caso você queira prevenir que seus arquivos e pastas sejam removidos ou modificados acidentalmente, basta você usar ferramentas definidas, por padrão, nos sistemas Linux.

Existe uma ferramenta de linha de comando chamado **chattr** (&#8220;Change Attribute&#8221;) que pode ser usado para impedir que arquivos e pastas sejam excluídos acidentalmente e até alterados sem sua permissão. Ele aplica certos atributos a um arquivo ou pasta que outros usuários não podem excluir ou modificá-los, acidentalmente ou intencionalmente, mesmo como usuário root.

**AVISO**
***
> Em sistemas de arquivos Linux, como o ext2, ext3, ext4 e o btrfs suportam todas os parâmetros disponíveis. 
> Assim, existem alguns sistemas de arquivos Linux que podem não suportar todas as funcionalidades que o <strong>chattr</strong> pode oferecer!
***

Por padrão, o **chattr** está disponível na maioria das distribuições Linux existentes:

{{< highlight Bash shell scripts >}}
$ chattr [operador] [chave] [nome do arquivo]
{{< /highlight >}}

#### 1. Impedir modificação e exclusão, acidental, de arquivo ou pasta

{{< highlight Bash shell scripts >}}
$ sudo chattr +i arquivo.txt
{{< /highlight >}}

Verifique os atributos do arquivo:

{{< highlight Bash shell scripts >}}
$  lsattr arquivo.txt
{{< /highlight >}}

{{< highlight Bash shell scripts >}}
--i------ arquivo.txt
{{< /highlight >}}

Tente remover o arquivo (usuário normal ou root):

{{< highlight Bash shell scripts >}}
$  sudo rm -f arquivo.txt
{{< /highlight >}}

{{< highlight Bash shell scripts >}}
  rm: não foi possível remover 'arquivo.txt': Operação não permitida
{{< /highlight >}}

Para reverter a operação:

{{< highlight Bash shell scripts >}}
$  sudo chattr -i arquivo.txt
{{< /highlight >}}

No caso de pastas, use o parâmetro -R:

{{< highlight Bash shell scripts >}}
$  sudo chattr -R +i /home/ricardo/pasta/
{{< /highlight >}}

#### 2.Permitir apenas modificação (inserção de dados) em um arquivo

Suponha que você só queira permitir que todos adicionem dados em um arquivo sem alterar ou modificar os dados já existentes. Você pode usar o atributo &#8216;a&#8217; da seguinte forma:

{{< highlight Bash shell scripts >}}
$  sudo chattr +a arquivo.txt
{{< /highlight >}}

Verifique os atributos do arquivo:

{{< highlight Bash shell scripts >}}
$  lsattr arquivo.txt
{{< /highlight >}}

{{< highlight Bash shell scripts >}}
--a---------- arquivo.txt
{{< /highlight >}}

Tente remover o arquivo (usuário normal ou root):

{{< highlight Bash shell scripts >}}
  sudo rm -f arquivo.txt
{{< /highlight >}}

{{< highlight Bash shell scripts >}}
  rm: não foi possível remover &#8216;arquivo.txt&#8217;: Operação não permitida
{{< /highlight >}}

Tente adicionar um conteúdo ao arquivo:

{{< highlight Bash shell scripts >}}
$  echo "texto inserido" >> arquivo.txt
{{< /highlight >}}

Para reverter a operação:

{{< highlight Bash shell scripts >}}
$  sudo chattr -a arquivo.txt
{{< /highlight >}}


## Considerações

Essa técnica pode ser útil para proteger os arquivos e dados importantes do sistema. Inclusive, de você mesmo! Pois, evita que informações sejam modificadas ou apagadas, acidentalmente.

Caso queira algo mais completo para segurança dos seus arquivos, use **<a href="https://linuxdescomplicado.com.br/2016/09/saiba-como-enviar-e-receber-informacoes-criptografadas-no-linux-usando-gnupg.html" target="_blank" rel="noopener noreferrer">técnicas de encriptação</a>**, por exemplo!
