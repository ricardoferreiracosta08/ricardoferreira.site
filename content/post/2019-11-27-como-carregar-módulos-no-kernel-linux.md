---
draft: false
title: 'Como carregar módulos no Kernel Linux '
seotitle: Como carregar módulos no Kernel Linux
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
#image
thumbnailImage: "https://lh3.googleusercontent.com/lQbTDmpqQA3mubRFOJ9Bdq7cySfxLnP7jDq8lBG2A_z1A3s5RtLIfBBhv8kk2xNVU6LqamgvdFUcjI4hmwWGIWLZCxjFlaiVroBLvYmkVK0BpabD_gr0IkdSeDot9KsquNj2vURMac4dLi_BCoLhiHU5uLMk5buyA_F832BS-B7sEZpVBxRtUNABJvV_QMTS1Gq5d4MfqBZFDROA6mnG9tdaf_bDIvUX_kA37OznMk63tpOV5je6-E_BoVYV4LfI8rCtG_yrRHSwRClDCpC4aeCveXqXdPbQGx4JgBc1O5JqAFNv1cGKkyiP8eDi95Ln1RPX_EUnsaZ5C6ZZlGuWrchN5wrLnVuhaIPIJQGfHW7NPeFzw---aDFUUtBQNEwzsWh8cyhrQRUtGfl1zIV2tzQV-eAAuM433-BD4Cx5xRL-g9rDhc3iiGc6-GvQTzu6PTepYVqQM_d9sVFEYfEb6uaP8Bs89Ci1w6-g5RcZy1wGMBop4ezpPrManeVIAlWqrg4a6A2O4CEMlf81XeY89GQvNvOwAoIxH8K8pj4_UHzFXQ1Xd9CCrOOspyaP9g-Yz5mTYdBF0LoVHTvRfSSPTWmwTjLnGCc22cZvWGzhXmaIWyJtr9x6FFNhiZT5jjlWvIasNWKjXKf3sZ0d-pKhq0IlfVfaeCVH991PxRSkgqqSGv4HwZxxW1o=w1280-h720-no"
thumbnailImagePosition: left
# coverImage:
# coverCaption: Foto de ...
# coverSize: partial
# somente se nao tiver thumb definido - ==> autoThumbnailImage: true
categories:
  - LinuxDescomplicado
tags:
  - kernel
  - lsmod
  - modprobe
  - terminal
keywords:
  - linux
  - kernel
  - modprobe
  - lsmod
  - proc
---
{{< youtube wFwOplqkKAM >}}

Nesse vídeo, eu mostro um exemplo prático de como manipular (load e unload) módulos no Kernel Linux. 

Usando o lsmod e a leitura do /proc/filesystems, capturo os módulos carregados no sistema. Com o modprobe carrego o módulo isofs (iso9660), previamente suportado, no meu Kernel LTS 4.19.84-1, disponibilizado no diretório /lib/modules/$(uname -r)/kernel/fs/isofs/. 

Por fim, removo o módulo usando o "modprobe -r" 
