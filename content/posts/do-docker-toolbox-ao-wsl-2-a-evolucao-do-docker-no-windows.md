---
draft: false
title: Do Docker Toolbox ao WSL 2 - a Evolução do Docker no Windows
subtitle: Um breve histórico
description: >-
  Breve histórico do Docker no Windows. Do Docker ToolBox ao WSL 2
summary: >-
  Depois do anúncio do Windows Subystem for Linux (WSL) em 2016, a Microsoft
  divulga, em 2019, nova versão do subsistema que permite rodar um Kernel Linux
  direto no Windows, sem recursos de virtualização. E isso impacta direto como
  containers Docker rodarão no Windows 10.
slug: do-docker-toolbox-ao-wsl-2-a-evolucao-do-docker-no-windows
date: 2019-11-05T23:29:33.000Z
image: /images/windows-10-docker.jpg
categories:
  - Docker
  - Windows
tags:
  - wsl
keywords:
  - wsl
  - container
  - windows
  - docker
---
Depois do anúncio do Windows Subystem for Linux (WSL) em 2016, a Microsoft divulga, em 2019, nova versão do subsistema que permite rodar um Kernel Linux direto no Windows, sem recursos de virtualização. E isso impacta direto como [**containers Docker**](https://www.udemy.com/course/docker-introducao-a-administracao-de-containers/) rodarão no Windows 10.

## Contextualizando

Primeiro suporte ao Docker no Windows se deu pelo [Docker Toolbox](https://docs.docker.com/toolbox/overview/), obsoleto e substituído pelo [Docker for Windows](https://docs.docker.com/docker-for-windows/). Ambos, rodando em máquina virtual (VM) com suporte via VirtualBox e Hyper-V, respectivamente.

Em 2016, surgiu o WSL oferecendo uma camada de compatibilidade para gerar binários executáveis do Linux “nativamente” no Windows 10. Fornecendo uma interface de núcleo compatível com o kernel Linux, ela usava bibliotecas do Kernel Windows (ou seja, sem nenhum código Linux).

Mesmo assim, **era impossível para executar** a Docker Engine e o [Kubernetes](https://www.profissionaisti.com.br/2018/07/o-que-e-o-kubernetes-e-sua-importancia/ "O que é o Kubernetes e sua importância"), por exemplo, diretamente dentro do WSL. Em vez disso, a Docker desenvolveu uma solução alternativa usando as VMs do Hyper-V e o LinuxKit para obter a perfeita integração consolidada atualmente – o [Docker for Windows](https://docs.docker.com/docker-for-windows/).

Então, chegamos ao WSL 2, lançado em junho de 2019 na versão Preview Build 18917 (20H1) do [programa Windows Insider](https://insider.windows.com/pt-br/), que permite aos usuários se inscreverem para contribuir pelo desenvolvimento do Windows 10. Em resumo, ao invés de usar a emulação, o WSL 2 usa realmente um kernel Linux rodando dentro de uma VM leve. Embora o WSL 2 use tecnologia de virtualização, ele não é uma Virtual Machine. Mas, será gerenciado e executado, como tal, “por baixo do capô”, sem intervenção direta do usuário.

**Recomendo que leia:**\
[WSL 2 – entenda a nova versão do subsistema que permite rodar um Kernel Linux no Windows 10](https://www.linuxdescomplicado.com.br/2019/06/wsl-2-entenda-a-nova-versao-do-subsistema-que-permite-rodar-um-kernel-linux-no-windows.html)

## Docker no Windows

Para a Docker, conforme [publicação oficial](https://engineering.docker.com/2019/06/docker-hearts-wsl-2/), essa abordagem é arquitetonicamente muito próxima do que é feito com o LinuxKit e o Hyper-V hoje, com o benefício adicional de ser mais leve e mais integrado ao Windows do que o Docker pode fornecer sozinho.

[![wsl2_2_smaller](../../../images/wsl2_2_smaller.gif)](https://engineering.docker.com/2019/06/docker-hearts-wsl-2/)

Para eles, o WSL 2 veio facilitar a intraoperabilidade do Docker com o Windows, deixar o desenvolvimento e a execução de [containers Docker](https://click.linksynergy.com/deeplink?id=/rNXZOKZPuM&mid=39197&murl=https%3A%2F%2Fwww.udemy.com%2Fdocker-introducao-a-administracao-de-containers%2F) mais rápidos.

> The Docker daemon runs well on it with great performance, and the time it takes from a cold boot to have dockerd running in WSL 2 is around 2 seconds on our developer machines. We are very excited about this technology, and we are happy to announce that we are working on a new version of Docker Desktop leveraging WSL 2, with a public preview in July. It will make the Docker experience for developing with containers even greater, unlock new capabilities, and because WSL 2 works on Windows 10 Home edition, so will Docker Desktop.\
> Via _[Docker hearts WSL 2](https://engineering.docker.com/2019/06/docker-hearts-wsl-2/)_

## O Futuro

Como o WSL 2 ainda está em preview, a Docker já planeja substituir a VM do Hyper-V, suportado no Docker for Windows, por um pacote de integração que fornecerá os recursos já existentes, contudo com suporte nativo ao WSL 2. Este pacote de integração conterá os componentes necessários para executar o Docker e o Kubernetes, bem como as ferramentas CLI usadas para interagir com esses componentes no WSL 2. Em seguida, poderemos introduzir um novo recurso com os espaços de trabalho do Docker Desktop: Linux.

Além disso, com a **integração do WSL 2**, você ainda terá interação maior com programas Linux em execução no WSL. Isso tem um grande impacto para os desenvolvedores que trabalham em projetos voltados para um ambiente Linux.

![runwsl-1024x876](../../../images/runwsl-1024x876.gif)

Por fim, usuários do Windows poderão colocar seus arquivos de aplicações diretamente no sistema de arquivos Linux para aproveitar os benefícios de desempenho de arquivos. Isso muda completamente a maneira como era feito antes; já que eles deviam ser salvos em sua unidade C ao usar o WSL.

Para ler mais sobre as principais mudanças, consulte a documentação oficial [aqui](https://docs.microsoft.com/en-us/windows/wsl/wsl2-ux-changes) e nota oficial da Docker sobre o assunto [aqui](https://engineering.docker.com/2019/06/docker-hearts-wsl-2/).
