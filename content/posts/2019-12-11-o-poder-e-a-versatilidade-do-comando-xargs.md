---
draft: false
title: O poder e a versatilidade do comando xargs
subtitle: Existem comandos Linux e existe o xargs
description: >-
  O comando xargs é um comando para construir pipelines de execução usando os
  fluxos de dados padrão. Ele tem função primeira receber uma entrada de uma
  lista de parâmetros de outro comando e passá-la para a execução de outro
  comando – isso tudo numa única sentença, através do uso do pipeline.
summary: >-
  Embora todos os comandos do Linux tenham os três fluxos padrão, nem todos
  aceitam o stdout de outro comando como entrada para sua entrada padrão. Isso
  significa que você não pode canalizar a entrada para eles. Daí o comando xargs
  entra na jogada
slug: o-poder-e-a-versatilidade-do-comando-xargs
date: 2019-12-11T18:35:51.240Z
image: /images/xargs_1140x570.jpg
categories:
  - LinuxDescomplicado
tags:
  - xargs
  - stdin
  - stdout
  - pipelines
keywords:
  - xargs
  - linux
  - stdin
  - stdout
  - stderr
  - pipelines
---
<div class="youtube">
<iframe class="video" src="https://www.youtube.com/embed/rw50a6-b9As" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>


Gosto muito da **[praticidade do terminal](https://www.linuxdescomplicado.com.br/2017/01/algumas-ferramentas-de-terminal-que-podem-ser-mais-praticas-do-que-os-aplicativos-graficos.html)**. Para alguns, um pavor; para outros uma obrigação. No meio disso, existem comandos que aumentam bastante nossa produtividade e que você não deveria refutar isso.

Entre diversos deles, destaco o **comando xargs**, um comando capaz de **aumentar sua produtividade**.

## Contextualizando

Todos os utilitários padrões do Linux possuem 3 **fluxos de dados** associados a eles:

* **1.** fluxo de entrada padrão (stdin),  
* **2.** fluxo de saída padrão (stdout),  
* **3.** fluxo de erro padrão (stderr)

Esses fluxos estão todos em **modo texto**. Enviamos **input (stdin)** para um comando usando texto, e a **resposta (stdout)** é escrita na janela do terminal como texto. **Mensagens de erro** também são exibidas no terminal como texto (stderr).

Um dos **grandes recursos** dos sistemas Linux e Unix é a **habilidade de canalizar** a saída padrão stdout de um comando para a entrada stdin de um segundo comando \o/ Assim, o **primeiro comando** não difere se sua saída não estar indo para um texto num terminal; e o **segundo comando** não distingue que sua entrada não esteja vindo de um teclado.

Embora **todos os comandos** do Linux tenham os três fluxos padrão, **nem todos aceitam** o stdout de outro comando como entrada para sua entrada padrão. Isso significa que você **não pode canalizar** a entrada para eles. Daí o comando xargs entra na jogada :)

## O comando xargs

O **comando xargs** é um comando para construir pipelines de execução usando os fluxos de dados padrão. O xargs aceitará entrada canalizada.

Ele tem função primeira **receber uma entrada** de uma lista de parâmetros de outro comando e **passá-la para a execução** de outro comando – isso tudo numa **única sentença**, através do uso do pipeline (|). Parece complexo, né?

Em resumo, o xargs pode pegar a saída de um comando e enviá-lo para outro como parâmetros ! :)

{{< highlight Bash shell scripts >}}
comando | xargs [opções] [comando] [lista_parâmetros comando anterior]
{{< /highlight >}}

## Exemplos

Como caso prático, mostro a leitura de arquivo de texto:

{{< highlight Bash shell scripts >}}
$ cat /home/ricardo/lista.txt

arquivo_1  
arquivo_2  
arquivo_3  
arquivo_4
{{< /highlight >}}

E se **canalizarmos a saída** do comando anterior através do comando xargs e pipeline (|)? Uma lista é exibida na janela do terminal:

{{< highlight Bash shell scripts >}}
$ cat /home/ricardo/lista.txt | xargs

arquivo_1 arquivo_2 arquivo_3 arquivo_4
{{< /highlight >}}

Assim, **esse recurso permite** que o xargs receba essa lista como parâmetros para outro(s) comando(s). Por exemplo: touch.

{{< highlight Bash shell scripts >}}
$ cat /home/ricardo/lista.txt | xargs touch
{{< /highlight >}}

Esse último comando se divide assim:

* **– cat directories.txt | :** Isso envia o conteúdo do arquivo lista.txt (todos os nomes de arquivos) para o xargs.  
* **– xargs touch:** cria (touch) todos os arquivos baseado na lista de parâmetros recebida do comando cat.

Por fim, dado a criação dos arquivos listados no arquivo, podemos usar a mesma estrutura para removê-los, simultaneamente, usando o comando rm:

{{< highlight Bash shell scripts >}}
$ cat /home/ricardo/lista.txt | xargs rm
{{< /highlight >}}

## Considerações

Diante do exposto, você percebe que essa canalização da entrada de dados de outro comando para o xargs pode aumentar sua produtividade, pois você **evita** repetições ou uso de scripts “complexos” para capturar saídas de outros comandos para, posteriormente, manipulá-los em outras estruturas de dados – _numa única sentença você faz **trabalhos simultâneos mais rapidamente**_.

É claro que o uso de **recursos de shell script** podem aumentar o nível de granularidade da lista de parâmetros canalizadas pelo xargs. Por exemplo:

{{< highlight Bash shell scripts >}}
$ ls -l | grep ” algo ” | cut -c55- | xargs rm
{{< /highlight >}}

Onde, o grep selecionou os arquivos que continham a cadeia “algo” no diretório corrente listado pelo ls -l. O comando cut pegou somente o nome dos arquivos, passando-os para a remoção pelo rm usando o comando xargs como sequencia.

Então, o poder e a versatilidade do xargs se torna cada vez mais marcante!

***

Via | [Dicas-l](http://www.dicas-l.com.br/cantinhodoshell/cantinhodoshell_20070226.php#.XUo8nHWYXmi) | [HowToGeek](https://www.howtogeek.com/435164/how-to-use-the-xargs-command-on-linux/)
