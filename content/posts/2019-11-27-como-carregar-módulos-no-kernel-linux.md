---
draft: false
title: 'Como carregar módulos no Kernel Linux '
subtitle: 'Uso do lsmod, modprobe e /procfs'
description: >-
  Usando o lsmod e a leitura do /proc/filesystems, capturo os módulos carregados
  no sistema. Com o modprobe carrego o módulo isofs (iso9660), previamente
  suportado, no meu Kernel LTS 4.19.84-1, disponibilizado no diretório
  /lib/modules/$(uname -r)/kernel/fs/isofs/. 
summary: >-
  Usando o lsmod e a leitura do /proc/filesystems, capturo os módulos carregados
  no sistema. Com o modprobe carrego o módulo isofs (iso9660), previamente
  suportado, no meu Kernel LTS 4.19.84-1, disponibilizado no diretório
  /lib/modules/$(uname -r)/kernel/fs/isofs/. 
slug: como-carregar-modulos-no-kernel-linux
date: 2019-11-27T15:16:22.052Z
image: /images/kernel-modulos-linux.png
categories:
  - LinuxDescomplicado
tags:
  - kernel
  - lsmod
  - modprobe
keywords:
  - linux
  - kernel
  - modprobe
  - lsmod
  - proc
---
Nesse vídeo, eu mostro um exemplo prático de como manipular (load e unload) módulos no Kernel Linux. 

Usando o lsmod e a leitura do /proc/filesystems, capturo os módulos carregados no sistema. Com o modprobe carrego o módulo isofs (iso9660), previamente suportado, no meu Kernel LTS 4.19.84-1, disponibilizado no diretório /lib/modules/$(uname -r)/kernel/fs/isofs/. 

Por fim, removo o módulo usando o "modprobe -r" 

<iframe width="960" height="515" src="https://www.youtube.com/embed/wFwOplqkKAM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
