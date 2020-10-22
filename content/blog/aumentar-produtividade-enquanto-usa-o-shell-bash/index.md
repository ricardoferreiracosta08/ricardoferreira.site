---
draft: false
title: 8 dicas que eu uso para aumentar minha produtividade no shell Bash
seotitle: Dicas para você aumentar sua produtividade enquanto usa o shell Bash
subtitle: Alguns "hacks"
description: >-
  Algumas dicas que podem ser muito úteis para você aumentar sua produtividade
  ao usar o shell bash. Maneiras para ser mais eficiente em suas tarefas.
summary: >-
  Algumas dicas que podem ser muito úteis para você aumentar sua produtividade
  ao usar o shell bash. Maneiras para ser mais eficiente em suas tarefas.
slug: aumentar-produtividade-enquanto-usa-o-shell-bash
images: 
  - 2019/12/aumentar-produtividade-enquanto-usa-o-shell-bash/cover.jpeg
date: 2019-12-09T18:00:43.472Z
categories:
  - Linux
tags:
  - shell
  - bash
  - terminal
keywords:
  - linux
  - bash
  - shell
  - terminal
---

{{< youtube cZ8vxzNQeMA >}}

Se sua rotina no Linux é definida por **executar comandos para agilizar suas operações**, essas dicas podem ser muito úteis para você aumentar sua produtividade ao usar o shell Bash. 

O terminal Linux é **amado por muitos e odiados por outros**. Basicamente, tudo que é feito no ambiente gráfico é possível fazer no terminal Linux. Mas, claro nem todos estão dispostos a abdicar de uma vida “tranquila” para ficar digitando comandos em terminal. 

Então, para que os estão dispostos, apresento maneiras para executar menos comandos e ser **mais eficiente em suas tarefas** :)

## Shell Bash

Primeiramente, o **shell (ou interpretador de linha de comando)** é um módulo que atua como camada externa (“concha“) entre o usuário e o sistema operacional. Existem **diversos tipos** de shell. O primeiro deles foi o **Bourne shell (sh)** que oferecia diversos comandos internos que permitiam ao usuário solicitar chamadas ao sistema operacional. 

A partir daí houveram evoluções significativas do shell. Atualmente, a maioria dos sistemas Linux usam, por padrão, **uma evolução do Bourne shell, chamada Bash (Bourne Again Shell)**. O Bash, além das funcionalidades das versões anteriores, também implementa um linguagem simples de programação que permite o desenvolvimento de pequenos programas (os famosos shell scripts).

<!--**RECOMENDO QUE LEIA:** 

***

> [Saiba como aprender 20 comandos Linux em apenas alguns minutos](https://www.linuxdescomplicado.com.br/2016/05/saiba-como-aprender-20-comandos-linux-em-apenas-alguns-minutos.html) 

> [20 comandos Linux que você talvez não conheça](https://www.linuxdescomplicado.com.br/2013/11/20-comandos-linux-que-voce-talvez-nao.html) 

> [Muito além do kernel – conheça todos os elementos que formam a estrutura do sistema Linux](https://www.linuxdescomplicado.com.br/2016/09/muito-alem-do-kernel-conheca-todos-os-elementos-que-formam-a-estrutura-do-sistema-linux.html)

***
-->
Em resumo, o **shell** é um programa independente do usuário, **executado fora do kernel**, que fornece uma interface para interpretação de comandos. Ele permite a interação com o sistema executando comandos em uma **interface de texto (CLI)**. Mesmo que você esteja apenas usando o ambiente gráfico e nunca tenha precisado usar ou executar nenhum comando Linux, o shell está em constante execução. Quando você abrir o terminal de linha de comando, você verá o shell em pleno funcionamento :)😉

## Foco na produtividade

Aqui deixo algumas dicas que podem fazer com você seja mais produtivo **enquanto usa o shell Bash** (obviamente, não apenas estas). 

#### 1 - Diretório do usuário num instante

O til (~) é uma abreviação do diretório inicial do usuário logado no sistema. Isso significa que você **não precisa digitar o caminho completo para o diretório inicial**. Onde quer que você esteja no sistema de arquivos, você pode usar este comando para acessar o diretório inicial: 

{{< highlight Bash shell scripts >}}
$ pwd $ cd /usr/share/locale $ cd ~
{{< /highlight >}}

Também, é possível, executar **apenas o comando cd sem o caracter til** (~): "cd" ele retorna para o diretório do usuário vigente.

#### 2 - Múltiplos comandos de uma vez

Você pode digitar quantos comandos quiser na linha de comando, **de uma única vez**, desde que separe cada um deles com um ponto-e-vírgula (;) 

{{< highlight Bash shell scripts >}}
$ ls lista.txt ; cat lista.txt ; wc -l lista.txt
{{< /highlight >}}

Observe que o terceiro comando é executado mesmo se o segundo falhar, e assim por diante. Se você deseja **interromper a sequência de execução** se um comando falhar, use um e comercial duplo (&&) em vez de um ponto e vírgula:

{{< highlight Bash shell scripts >}}
$ ls lista.txt && cat lista.txt && wc -l lista.txt
{{< /highlight >}}

#### 3 - Execute o último comando rapidamente

Você costuma **usar as setas para cima e para baixo** para encontrar o comando e depois executá-lo? Isso leva muito tempo. Concorda? Use (!) ou (!!) para executar o último comando facilmente. No caso do (!) apenas **é preciso lembrar o nome do comando**.

{{< alert info no-icon >}}
**FIQUE SABENDO** 

Ao executar o comando "history" você verá diversos comandos com seus respectivos IDs. 
Execute "!ID" (sem aspas) e verá o comando ser executado novamente.
{{< /alert >}}


**Por exemplo:** ! cat executará seu último "cat lista.txt". Definitivamente, economiza muito tempo e também é **útil em shell diferente do bash shell** (como csh ou ksh), onde as setas para cima e para baixo geralmente não fornecem comandos anteriores. 

Por outro lado, você pode usar (!!) para **executar o último comando que você executou**, sem precisar "lembrar do comando". 

#### 4 - Uso do pipe (|)

Um "tubo" encadeia comandos juntos. Ele **pega a saída de um comando e a alimenta para o próximo como entrada**. O número de comandos canalizados (o comprimento da cadeia) é arbitrário. Aqui, usaremos cat para alimentar o conteúdo do arquivo lista.txt no "grep", que extrai qualquer linha que contenha um numeral "1" e exibe o resultado: 

{{< highlight Bash shell scripts >}}
$ cat lista.txt | grep 1
{{< /highlight >}}

#### 5 - Buscar pelo comando já executado mais rapidamente

[ADSENSE]

Use "CTRL + R" para encontrar o último comando correspondente ao que deseja executar novamente. Melhor momento que você sabe que executou o comando "[ls -l | grep ” algo ” | cut -c55- | xargs rm](https://www.linuxdescomplicado.com.br/2019/08/o-poder-e-a-versatilidade-do-comando-xargs.html)", alguma vez no passado, mas não lembra os parâmetros necessários para executá-lo, novamente. Basta pressionar o botão "CRTL + R" e digite as palavras que você tinha no seu último comando e o sistema encontrará esse comando para você... depois basta pressionar ENTER 

Assim, eu evito de usar o comando "history" para buscar os últimos comandos executados :)

#### 6 - Uso de apelidos para seus comandos mais usados

Para [criar "seus próprios" comandos](https://www.linuxdescomplicado.com.br/2015/06/criar-comandos-usando-alias.html) é preciso usar o recurso de Alias. A sua estrutura é bem simples, como segue:

{{< highlight Bash shell scripts >}}
$ alias nome_apelido=’comando com parâmetros‘
{{< /highlight >}}

Para criá-los, é preciso modificar o **arquivo .bashrc** que se encontra em **/home/NomeDoUsuário/.bashrc** (se o arquivo não existir, crie-o) e adicionar cada apelido no final do arquivo. 

Por fim, para gravar definitivamente esses apelidos, execute, no diretório home do usuário:

{{< highlight Bash shell scripts >}}
# source ~/.bashrc
{{< /highlight >}}

#### 7 - Navegar em dois diretórios rapidamente

Use o caracter (-) junto com o comando "cd" para **alternar entre um e outro**. Aliado a isso, você pode usar os comandos "pushd", que insere diretório para a pilha de diretórios para alternar, e o "popd", que retira da pilha o último diretório inserido.

#### 8 - Alguns atalhos de teclado

Sem o mouse parece possível apenas o uso das setas (esquerda e direita) para a **movimentação do cursor**. Entretanto, com algumas teclas de atalho é possível ser mais produtivo e ágil:

{{< highlight Bash shell scripts >}}
Ctrl + a - vá para o início da linha de comando. 
Ctrl + e - vai para o final da linha de comando. 
Ctrl + k - exclua do cursor até o final da linha de comando - economize muito tempo. Ctrl + u - exclua do cursor até o início da linha de comando, não a estou usando, mas ainda assim boa. 
Ctrl + w - excluir do cursor para o início da palavra (ou seja, excluir uma palavra para trás) 
Ctrl + y - cole a palavra ou o texto que foi cortado usando um dos atalhos de exclusão (como o acima) após o cursor 
Ctrl + xx - move entre o início da linha de comando e a posição atual do cursor (e vice-versa) 
Alt + b - recua uma palavra (ou vá para o início da palavra em que o cursor está ativado) 
Alt + f - avança uma palavra (ou vai para o final da palavra em que o cursor está ativado) 
Alt + d - excluir para o final da palavra começando no cursor (palavra inteira se o cursor estiver no início da palavra) 
Alt + c - coloque em maiúscula no final da palavra começando no cursor (palavra inteira se o cursor estiver no início da palavra) 
Alt + u - faz maiúsculas do cursor até o final da palavra 
Alt + l - faz minúsculas do cursor até o final da palavra 
Alt + t - troca a palavra atual pela anterior 
Ctrl + f - avança um caractere 
Ctrl + b - retrocede um caractere 
Ctrl + d - exclui caracteres sob o cursor 
Ctrl + h - exclui o caractere antes do cursor 
Ctrl + t - troca o caractere sob o cursor pelo anterior
{{< /highlight >}}

<!-- Via | [howtogeek](https://www.howtogeek.com/439199/15-special-characters-you-need-to-know-for-bash/) | [greenido](https://greenido.wordpress.com/2011/10/07/linux-bash-shortcuts-to-boost-your-productivity/) | [hackernoon](https://hackernoon.com/10-basic-tips-on-working-fast-in-unix-or-linux-terminal-5746ae42d277) -->
