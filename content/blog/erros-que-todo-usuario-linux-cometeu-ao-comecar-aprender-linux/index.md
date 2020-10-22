---
draft: false
title: Alguns erros que eu cometi quando comecei a aprender Linux
#seotitle: 5 Erros que todo usuário Linux cometeu ao aprender Linux
subtitle: Aprenda com algum dos meus erros
description: >-
  Todos os erros se concentram no terminal de comandos, pois lá está presente os maiores riscos para o sistema
summary: >-
  Todos os erros se concentram no terminal de comandos, pois lá está presente os maiores riscos para o sistema
slug: erros-que-todo-usuario-linux-cometeu-ao-comecar-aprender-linux
date: 2020-01-26T22:35:51.240Z
images:
  - 2020/01/erros-que-todo-usuario-linux-cometeu-ao-comecar-aprender-linux/cover.jpg
categories:
  - Linux
tags:
  - iniciante
keywords:
  - erros
  - terminal
  - linux
---

É importante **aprender novas habilidades** ao longo de sua vida – isso mantém sua mente ágil e o torna mais competitivo no mercado de trabalho.

Mas algumas habilidades são **mais difíceis** de aprender do que outras, especialmente aquelas que pequenos erros podem custar muito tempo e causar problemas inconvenientes quando você ainda está tentando aprender.

Inclusive, esse erro pode ser determinante para você “largar tudo” e “deixar para depois”, **desistindo de aprender Linux**.

## APRENDER LINUX

Erros sempre irão ser cometidos. Faz parte do **processo de aprendizagem**, independente em qual curva do conhecimento esteja. Por exemplo, se você está acostumado a trabalhar em uma **interface gráfica** do Windows ou MacOS, mudar para o Linux, com seus comandos **não familiares** digitados em um terminal, pode ter uma grande **complexidade para você**.

[ADSENSE]

Mas, **se não desiste** nesses pequenos obstáculos, as recompensas valerão a pena. Pois, muitas outras pessoas tiveram as mesmas ou outras dificuldades antes de você, e provavelmente, estão usando o Linux de alguma maneira, seja no trabalho ou no cotidiano.

Diante disso, digo que o percurso não será fácil e nem impossível, pois são dos erros que você deve ter convicção que o aprendizado está sendo provado. Portanto, compartilho com você alguns erros mais **comuns que todo usuário Linux cometeu ao começar aprender Linux**. Espero que ajude :)

## ERROS MAIS COMUNS

#### 1. Executar comandos sem conhecê-los

Além do risco de comprometer parte do sistema ou perder algum arquivo/configuração importante, você tende a ficar frustado com a falta de êxito ao tentar executar o comando.

Imagine você tentando uma busca textual no sistema usando o comando find! Por não ter noção completa da estrutura do comando, você, provavelmente, não terá o resultado esperado, colocando em dúvida o comando executado e ainda ficará relutante com alternativas, sejam gráficas ou via terminal.

Daí, também, vem o **preconceito que o terminal é difícil**. Pois, se você atropela o processo de aprendizado tudo fica mais complexo :/

#### 2. Copiar, colar e executar comandos sem devidos cuidados

Pegando gancho com o primeiro erro, esse se resume aos “apressados de plantão” – é proativo, pesquisa em fóruns e encontra o que precisa. Contudo, não verifica a estrutura básica do comando e tem o risco de algo dar errado.

Por isso, leia o comando primeiro e pelo menos tenha uma compreensão geral das ações que estão prestes a serem executadas. Especialmente se houver um comando de pipe. Se houver mais de um, existem muitos comandos “perigosos” que parecem inofensivos até você perceber o que eles podem fazer (por exemplo, rm , dd ) :/

Então, não conhecer o comando que você deseja executar culmina numa cadeia de problemas, mesmo para um usuário dito “avançado” – desde a frustração ao erro comprometedor.

#### 3. Não se preocupar com a dependência de pacotes e suas fontes

Quem nunca removeu um pacote do sistema e não verificou de que outros pacotes ele dependia? Apenas remover o que vem selecionado, por padrão, acaba fazendo com que alguns dos seus programas importantes falhem e fiquem indisponíveis.

Quando se estar começando, instalar, remover e atualizar pacotes é uma tarefa desapercebida, pois os grandes gerenciadores de pacotes existentes nos sistemas Linux, como apt, yum, pacman, dnf e outros; atendem muito bem suas “obrigações”. Contudo, eles não conhecem suas necessidades. Por isso, é fundamental que a mensagem informativa, com todos os pacotes que serão afetados, na instalação, remoção ou atualização, seja lida com cuidado; antes de confirmar (y/N) a operação.

#### 4. Usar o modo super-usuário “para tudo”

Para quem faz isso, parece evitar o retrabalho de informar o “sudo” e suas credencias toda vez que precisar. Tem gente que aumenta o tempo para ele solicitar a senha, dado uma vez informada no passado.

Contudo, esses mecanismos de mudança de modos de usuários são o segredo do sucesso dos sistemas Linux. O risco para se executar tudo em modo super-usuário (sudo), ou como root, é altíssimo. Para quem está começando, executar um comando nesses modos causam super exposições do sistema, podendo remover ou alterar um arquivo importante, sem ser alertado do risco, por exemplo.

#### 5. Conceder permissão completa “para tudo e todos”
Depois que se aprende as permissões em sistema de arquivos Linux, parece que o descuido aumenta. Quem nunca teve um problema e encontrou na internet como solução sendo “problema de permissão”? Daí, você concede a famosa permissão “777” :/

Primeiro, não existe “problema de permissão”. O controle de acesso via permissões é uma solução. O que acontece é o uso das permissões erradas no arquivo, em questão. Por isso, o correto é encontrar permissões adequadas para aquele arquivo ou pasta.

Existem permissões que deve ser concedidas somente para o dono do arquivo. Outras para o grupo e outros, e permissões somente de execução e não de escrita. Cada nuance dessas põe em risco a segurança do seu sistema, principalmente se feito em um recurso protegido pelo modo super-usuário :/

—

Assim, diante desses erros muito comuns, que erros você cometeu enquanto aprendia a usar o Linux? Compartilhe-os nos comentários.

