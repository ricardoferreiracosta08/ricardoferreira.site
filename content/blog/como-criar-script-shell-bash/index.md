--- 
draft: false
date: 2021-03-12T09:31:44-03:00
title: "Saiba como criar um script shell em 5 passos básicos"
subtitle: "Um bom começo"
description: "Vou apresentar uma maneira para escrever um Script Shell Bash seguindo boas práticas que otimizam seu trabalho"
summary: ""
slug: "criar-shell-script-bash-linux"
featured_image: ""
keywords:
  - shell
  - scprit
  - bash
images:
  - /2021/03/criar-shell-script-bash-linux/banner.jpeg
authors:
tags:
categories: 
  - Linux
externalLink: ""
series:
---

Vou apresentar uma maneira para escrever um Script Shell Bash seguindo boas práticas que otimizam seu trabalho. Para
esse artigo vou usar meu script de Backup disponível no meu GitHub 
[aqui](https://github.com/ricardoferreiracosta08/backup_restore-full-incr-dif_script_shell)

### 01 - Variáveis globais

No topo do arquivo, reserve um espaço para definir suas variáveis globais que serão usadas ao longo do script. 
Isso é interessante para você ter clareza e distinção das variáveis macros e as regras do negócio:

{{< highlight bash "style=dracula" >}}
# TOPO DO ARQUIVO
# ---------------------------
remote_ssh="192.168.122.69"
port_ssh="22"
user_ssh="root"
dir_backup_ssh="/mnt/backups"
dir_restore_ssh="/home/ricardo"
{{< /highlight >}}

### 02 - Uso de funções

No "coração do código", de acordo com o nível de complexidade do seu script você precisará reusar código para evitar linhas desnecessárias.
Uma boa solução para isso é a adoção de funções! Criou, chamou e usou

{{< highlight bash "style=dracula" >}}
.
.
.
incremental()
{
 
 if [ ! -f "$LOCAL_BACKUP/backupcompleto.tar.gz" ]; then
   echo -e "[Erro] Não existe Backup COMPLETO .................................. " 
   exit 1
 fi


 if tar -czvf $LOCAL_BACKUP/backup.inc$DIA.tar.gz -T $PASTAS_BACKUP -g $CONTROLE_INCREMENTAL 
 then
  echo -e "OK" | tee $monitor_file 
  rsync -avz -e ssh $LOCAL_BACKUP/backup.inc$DIA.tar.gz $user_ssh@$remote_ssh:$dir_backup_ssh 
 
 else
  echo -e "\nErro: durante compactação" 
  echo -e "FAIL" | tee $monitor_file
  exit 1
 fi
}
.
.
.
{{< /highlight >}}

### 03 - Passagem de parâmetros

Um bom exemplo disso é ao usar função.

Passar parâmetros para que ela receba uma ou mais variáveis fora do escopo de função, processe e retorne a saída é 
conduta básica para definir uma finalidade específica para a função:

{{< highlight bash "style=dracula" >}}
recuperar()
{
  backup=$1
  destino=$2

  if ! cat $LOCAL_BACKUP/$backup | tar -xvzf - -C $destino 1>>/dev/null 
  then
    exit 1
  fi
}

case $1 in
completo) completo ;;
recuperacao) menu_recuperar ;;
recuperar) recuperar $2 $3 ;;
*) exit 1 ;;
esac
{{< /highlight >}}

### 04 - Fluxo padrão redirecionado

Ninguém deseja ver cuspindo na tela, durante a execucação do script, saídas ou erros dos comandos executados.

Uma boa prática é redirecionar saídas padrões (stdout) ou saídas de erro (sdterr) para um arquivo de log ou no limbo

{{< highlight bash "style=dracula" >}}
tar -xvzf $backup_recupera -C $destino  >>1/dev/null
{{< /highlight >}}

### 05 - Status na saída

Para fins de tratamento é importante informar se o término do script foi dado de maneira esperado (exit 0) ou inesperado 
(exit 1)

Muito comum nas condicionais de verificação de execução!

{{< highlight bash "style=dracula" >}}
if tar -czvf $PATH_BACKUP -T $PASTAS_BACKUP 
   then
     echo "OK" | tee $MONITOR_FILE
   else
     echo "ERRO" | tee  $MONITOR_FILE
     exit 1
fi
{{< /highlight >}}
