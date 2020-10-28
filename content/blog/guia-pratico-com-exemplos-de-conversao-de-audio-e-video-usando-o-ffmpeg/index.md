---
draft: true
title: Guia prático de conversão de áudio e vídeo usando o FFmpeg
#seotitle: Guia prático com exemplos de conversão de áudio e vídeo usando o FFmpeg
subtitle: O poder do FFmpeg
description: >-
     FFmpeg é um excelente framework, de código aberto, completo que lida com arquivos de áudio e vídeo. Por isso, 
     guia prático com exemplos que mostram o poder dessa ferramenta!
summary: >-
     FFmpeg é um excelente framework, de código aberto, completo que lida com arquivos de áudio e vídeo. Por isso, 
     guia prático com exemplos que mostram o poder dessa ferramenta!
readingtime: '3'
slug: guia-pratico-com-exemplos-de-conversao-de-audio-e-video-usando-o-ffmpeg
date: 2020-02-03T11:25:12.051Z
#image
images:
  - 2020/02/
categories:
  - Linux
tags:
  - ffmpeg
  - video
  - audio
  - terminal
keywords:
  - linux
  - ffmpeg
  - video
  - audio
  - terminal
---

FFmpeg é um excelente framework, de código aberto, completo que lida com arquivos de áudio e vídeo. Em outras palavras, é possível converter um formato multimídia para outro, extrair áudio de um vídeo, compactar um vídeo e até mesmo extrair imagens de um vídeo; e diversas outras coisas.

É escrito, principalmente, na linguagem de programação C; juntamente com diversas bibliotecas livres. Sendo assim, resolvi criar um guia prático com exemplos que mostram o poder dessa ferramenta!

[ADSENSE]

## FFMPEG

Como dito, o [FFmpeg](https://ffmpeg.org/) é um framework open source multiplataforma que oferece uma das melhores estruturas para manipulação de dados multimídia (áudio/vídeo) existentes. Pois, ele contém várias ferramentas disponíveis para diferentes tarefas. Por exemplo:

– [ffplay](https://ffmpeg.org/ffplay.html) – um reprodutor de mídia leve que pode ser usado para reproduzir arquivos de áudio/vídeo;

– [ffmpeg](https://ffmpeg.org/) – um conversor para diferentes formatos de arquivo áudio/vídeo;

– [ffserver](https://ffmpeg.org/ffserver.html) – pode ser usado para transmitir streaming ao vivo;

– [ffprobe](https://ffmpeg.org/ffprobe.html) – é capaz de analisar stream multimídia.

Assim, com suporte ao Linux, Mac OS X, Microsoft Windows, BSDs, Solaris; o FFmpeg é um framework multimédia capaz de decodificar, codificar, transcodificar, mux, demux, transmitir, filtrar e mais…. Inclusive, ele suporta os formatos áudio/vídeo mais diversos possíveis.

De acordo com a descrição do site oficial, a razão para ter um framework multimídia tão completo é a combinação das melhores opções de software livre disponíveis.

## CONVERSÃO DE ÁUDIO E VÍDEO USANDO O FFMPEG

#### 1 – Obter informações avançadas de um vídeo

Para fazer isso, a ferramenta ffprobe deve ser usada. De acordo com a documentação oficial, esta ferramenta reúne informações de streams multimídia e exibe-os de forma legível por um humano (claro, que entenda o assunto):

{{< highlight Bash shell scripts >}}
ffprobe -show_format -show_streams ARQUIVO.mp4
{{< /highlight >}}


#### 2 – Obter informações sobre o arquivo multimídia
Para obter informações sobre um arquivo (por exemplo, video.mp4), execute o seguinte comando:

{{< highlight Bash shell scripts >}}
ffmpeg -i video.mp4
{{< /highlight >}}

#### 3 – Extrair o áudio de vídeo MP4
Esse recurso permite salvar o arquivo de áudio de um vídeo MP4:

{{< highlight Bash shell scripts >}}
ffmpeg -i video.mp4 -vn -ab 128 audiovideo.mp3
{{< /highlight >}}

Onde,

“-i” – significa a inserção do arquivo de entrada;
“-vn” – significa que não inclui o vídeo na saída;
“-ab” – usado para salvar o áudio em 128Kbps – pode ser 256kbps;

#### 4 – Alterar dimensões do vídeo

Nesse exemplo, um vídeo com dimensões 1920×1080 será convertido para um com dimensões de 640×480:

{{< highlight Bash shell scripts >}}
ffmpeg -i video.mp4 -s 640×480 -c:a copy videoalterado.mp4
{{< /highlight >}}

#### 5 – Extrair uma imagem específica de um vídeo (Thumbnail)

É possível extrair imagem específica de determinado trecho do vídeo:

{{< highlight Bash shell scripts >}}
ffmpeg -i video.mp4 -ss 00:00:14.435 -vframes 1 imagem.png
{{< /highlight >}}

Onde,

“-i” – – significa a inserção do arquivo de entrada;
“-ss” – tempo em segundos depois do início do vídeo;
“-vframes” – informa a quantidade de frames a serem extraídos. Nesse caso, 1 frame (quadro);

#### 6 – Adicionar imagem de poster para um arquivo de áudio

Muito útil para fazer upload para sites/serviços de streaming de áudio que oferecem esse tipo de recurso:

{{< highlight Bash shell scripts >}}
ffmpeg -loop 1 -i poster.jpg -i audio.mp3 -c:v libx264 -c:a aac -strict experimental -b:a 192k -shortest arquivosaida.mp4
{{< /highlight >}}

#### 7 – Exportar várias imagens do vídeo

{{< highlight Bash shell scripts >}}
ffmpeg -i arquivo.mp4 imagem%d.jpg
{{< /highlight >}}

A saída vai ficar assim: imagem01.jpg, imagem02.jpg, imagem03.jpg e assim por diante 😉

#### 8 – Converter várias imagens em um vídeo

Dado um diretório repleto de imagens, com um padrão no nome do arquivo (imagem01.jpg, imagem02.jpg,…), é possível criar um vídeo a partir delas:

{{< highlight Bash shell scripts >}}
ffmpeg -f image2 -i imagem%d.jpg videodeimagem.mpg
{{< /highlight >}}

#### 9 – Cortar um vídeo em pedaços menores

Dado um vídeo, é possível criar “miniaturas” dele e gerar um novo vídeo:

{{< highlight Bash shell scripts >}}
ffmpeg -i video.mp4 -ss 00:00:45 -codec copy -t 40 videomenor.mp4
{{< /highlight >}}

Onde,

“-i” – – significa a inserção do arquivo de entrada;
“-ss” – tempo em segundos depois do início do vídeo;
“-t” – duração do vídeo. Nesse caso, 40s;

#### 10 – “Misturar” com um áudio com um vídeo

{{< highlight Bash shell scripts >}}
ffmpeg -i audio.mp3 -i video.avi video_audio_mix.mpg
{{< /highlight >}}

#### 11 – Verificar qualidade do áudio e vídeo

Para verificar a qualidade técnica do vídeo, use a ferramenta ffplay:

{{< highlight Bash shell scripts >}}
ffplay video.mp4
{{< /highlight >}}

Um player “simples” de vídeo será iniciado e informações do vídeo serão mostradas no terminal, simultaneamente!

Para verificar a qualidade técnica do áudio:

{{< highlight Bash shell scripts >}}
fplay audio.mp3
{{< /highlight >}}

#### 12 – Adicionar legenda a um vídeo

Caso possua o arquivo “legenda.srt” de legenda, use o seguinte comando para adicioná-la ao vídeo:

{{< highlight Bash shell scripts >}}
ffmpeg -i video.mp4 -i legenda.srt -map 0 -map 1 -c copy -c:v libx264 -crf 23 -preset veryfast video-legenda.mkv
{{< /highlight >}}

#### 13 – Cortar aúdio

{{< highlight Bash shell scripts >}}
ffmpeg -ss 00:00:15 -t 45 -i audio.mp3 audiocortado.mp3
{{< /highlight >}}

#### 14 – Converter vídeo MP4 para AVI

{{< highlight Bash shell scripts >}}
ffmpeg -i video.mp4 video.avi
{{< /highlight >}}

Ou vice-versa:

{{< highlight Bash shell scripts >}}
ffmpeg -i video.avi video.mp4
{{< /highlight >}}

#### 15 – Converter um vídeo para outro formato

Para conhecer os formatos suportados pelo ffmpeg, execute:

{{< highlight Bash shell scripts >}}
ffmpeg -formats
{{< /highlight >}}

Depois, prossiga para a conversão. Seguem alguns exemplos:

MP4/WMV

{{< highlight Bash shell scripts >}}
ffmpeg -ivideo.mp4 -c:v libx264 video.wmv
{{< /highlight >}}

FLV/MPG

{{< highlight Bash shell scripts >}}
ffmpeg -i video.flv video.mpg
{{< /highlight >}}

AVI/MPEG

{{< highlight Bash shell scripts >}}
ffmpeg -i video.avi -target pal-dvd -ps 2000000000 -aspect 16:9 video.mpeg
{{< /highlight >}}

#### 16 – Unir arquivos de vídeo

{{< highlight Bash shell scripts >}}
ffmpeg -f concat -i lista.txt -c copy arquivo.mp4
{{< /highlight >}}

Onde,

“lista.txt” é o arquivo que contém o caminho de todos os vídeos:

/home/linux10complica/video1.mp4
/home/linux10complica/video2.mp4
/home/linux10complica/video3.mp4

#### 17 – Remover áudio de vídeo

É possível remover o áudio de um vídeo e deixá-lo “mudo”:

{{< highlight Bash shell scripts >}}
ffmpeg -i video.mp4 -an videomudo.mp4
{{< /highlight >}}

#### 18 - Gravar área de trabalho

{{< highlight Bash shell scripts >}}
ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq /tmp/minha-area-trabalho.mp4
{{< /highlight >}}

***

## SAIBA MAIS

[FFmpeg – Site Oficial](https://ffmpeg.org/)
