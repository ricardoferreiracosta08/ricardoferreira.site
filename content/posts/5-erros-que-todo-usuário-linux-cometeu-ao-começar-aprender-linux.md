+++
author = "Ricardo Ferreira"
authorbio = "Criador e administrador desse portal para Sysadmin Linux. Possui mais de 6 anos de experiência com administração de servidores Linux. Pretende compartilhar todo seu conhecimento e experiência, da mesma forma como no Linux Descomplicado, onde também é criador e administrador ;-)"
authorgravatar = "1a0f8133a8142fc8d8421a985eefd7aa"
authorwebsite = "http://sysadmin.linuxdescomplicado.com.br/sobre/"
categories = ["webserver", "networking"]
date = "2016-05-12T18:23:58-03:00"
lastmod = 2018-04-23T21:41:23-03:00
description = "O Firewall IPTables é um firewall de nível de pacotes, ou seja, usa parâmetros, como porta/endereço de origem/destino, estado da conexão, e outros para fazer a filtragem e segurança na rede. Em suma, o IPTables tem inúmeras possibilidades de controle oferecidas pelos recursos de filtragem. "
image = "images/Regras-IPtables-conhecer.png"
keywords = ["iptables", "firewall", "linux", "segurança", "security"]
slug = "10-regras-do-firewall-iptables-que-todo-sysadmin-linux-deve-conhecer"
tags = ["webserver", "firewall", "security", "segurança"]
title = "10 Regras do Firewall IPTables que todo sysadmin Linux deve conhecer"
subtitle = "Quanto mais melhor, pode crer!"
summary = "My compact summary"
+++

É importante **aprender novas habilidades** ao longo de sua vida — isso mantém
sua mente ágil e o torna mais competitivo no mercado de trabalho.

#### Se ainda os comete, reveja-os

{{< highlight Bash shell scripts >}}
$ goaccess -f /var/log/apache2/access.log
{{< /highlight >}}


Mas algumas habilidades são** mais difíceis** de aprender do que outras,
especialmente aquelas que pequenos erros podem custar muito tempo e causar
problemas inconvenientes quando você ainda está tentando aprender.

Inclusive, esse erro pode ser determinante para você “largar tudo” e “deixar
para depois”, **desistindo de aprender Linux**.

### APRENDER LINUX

Erros sempre irão ser cometidos. Faz parte do **processo de aprendizagem**,
independente em qual curva do conhecimento esteja. Por exemplo, se você está
acostumado a trabalhar em uma **interface gráfica** do Windows ou MacOS, mudar
para o Linux, com seus [comandos não
familiares](https://www.linuxdescomplicado.com.br/2017/01/algumas-ferramentas-de-terminal-que-podem-ser-mais-praticas-do-que-os-aplicativos-graficos.html)
digitados em um terminal, pode ter uma grande **complexidade para você**.

> **RECOMENDO QUE LEIA**<br>  → [10 coisas que você deve saber caso esteja
> começando com o
Linux](https://www.linuxdescomplicado.com.br/2017/09/10-coisas-que-voce-deve-saber-caso-esteja-comecando-com-o-linux.html)<br>
→ [Saiba como aprender 20 comandos Linux em apenas alguns
minutos](https://www.linuxdescomplicado.com.br/2016/05/saiba-como-aprender-20-comandos-linux-em-apenas-alguns-minutos.html)<br>
→ [Algumas ferramentas de terminal que podem ser mais práticas do que os
aplicativos
gráficos](https://www.linuxdescomplicado.com.br/2017/01/algumas-ferramentas-de-terminal-que-podem-ser-mais-praticas-do-que-os-aplicativos-graficos.html)

Mas, **se não desiste** nesses pequenos obstáculos, as recompensas valerão a
pena. Pois, muitas outras pessoas tiveram as mesmas ou outras dificuldades antes
de você, e provavelmente, estão usando o Linux de alguma maneira, seja no
trabalho ou no cotidiano.

Diante disso, digo que o percurso não será fácil e nem impossível, pois são dos
erros que você deve ter convicção que o aprendizado está sendo provado.
Portanto, compartilho com você alguns **erros mais comuns que todo usuário Linux
cometeu ao começar aprender Linux**. Espero que ajude :)

### ERROS MAIS COMUNS

### 1. Executar comandos sem conhecê-los

Além do risco de comprometer parte do sistema ou perder algum
arquivo/configuração importante, você tende a ficar frustado com a falta de
êxito ao tentar executar o comando.

Imagine você tentando uma busca textual no sistema usando o [comando
find](https://www.linuxdescomplicado.com.br/2013/07/comandos-linux-encontre-tudo-que.html)!
Por não ter noção completa da estrutura do comando, você, provavelmente, não
terá o resultado esperado, colocando em dúvida o comando executado e ainda
ficará relutante com alternativas, sejam gráficas ou via terminal.

> **RECOMENDO QUE LEIA**<br>  → [Comandos Linux: Encontre tudo que procura
> dominando o comando
find](https://www.linuxdescomplicado.com.br/2013/07/comandos-linux-encontre-tudo-que.html)

Daí, também, vem o **preconceito que o terminal é difícil**. Pois, se você
atropela o processo de aprendizado tudo fica mais complexo :/

### 2. Copiar, colar e executar comandos sem devidos cuidados

Pegando gancho com o primeiro erro, esse se **resume aos “apressados de
plantão”** — é proativo, pesquisa em fóruns e encontra o que precisa. Contudo,
não verifica a estrutura básica do comando e tem o risco de algo dar errado.

Por isso, **leia o comando primeiro** e pelo menos tenha uma compreensão geral
das ações que estão prestes a serem executadas. Especialmente se houver um
**comando de pipe**. Se houver mais de um, existem muitos comandos “perigosos”
que parecem inofensivos até você perceber o que eles podem fazer (por exemplo,
rm , dd ) :/

> **RECOMENDO QUE LEIA**<br>  → [Não sabe o que um determinado comando Linux faz?!
> Deixa que o ExplainShell explica pra
você](https://www.linuxdescomplicado.com.br/2014/04/nao-sabe-o-que-um-comando-linux-faz.html)

Por isso, não conhecer o comando que você deseja executar **culmina numa cadeia
de problemas**, mesmo para um usuário dito “avançado” — desde a frustração ao
erro comprometedor.

### 3. Não se preocupar com a dependência de pacotes e suas fontes

Quem nunca removeu um pacote do sistema e não verificou de que outros pacotes
ele dependia? Apenas remover o que vem selecionado, por padrão, acaba fazendo
com que alguns dos seus programas importantes falhem e fiquem indisponíveis.

**Quando se estar começando**, instalar, remover e atualizar pacotes é uma**
tarefa desapercebida**, pois os grandes gerenciadores de pacotes existentes nos
sistemas Linux, como
[apt](https://www.diolinux.com.br/2016/06/qual-diferenca-entre-apt-e-apt-get.html),
yum, pacman, dnf e outros; atendem muito bem suas “obrigações”. Contudo, eles
não conhecem suas necessidades. Por isso, é fundamental que a **mensagem
informativa**, com todos os pacotes que serão afetados, na instalação, remoção
ou atualização, **seja lida com cuidado**; antes de confirmar (y/N) a operação.

### 4. Usar o modo super-usuário “para tudo”

Para quem faz isso, **parece evitar o retrabalho** de informar o “sudo” e suas
credencias toda vez que precisar. Tem gente que aumenta o tempo para ele
solicitar a senha, dado uma vez informada no passado.

Contudo, **esses mecanismos** de mudança de modos de usuários são o **segredo do
sucesso** dos sistemas Linux. O risco para se executar tudo em modo
super-usuário (sudo), ou como root, é altíssimo. Para quem está começando,
executar um comando nesses modos **causam super exposições do sistema**, podendo
remover ou alterar um arquivo importante, sem ser alertado do risco, por
exemplo.

> **RECOMENDO QUE LEIA**<br>  → [Por que usuários Linux devem se preocupar com
> riscos em segurança e o que pode ser feito para se
proteger](https://www.linuxdescomplicado.com.br/2017/02/por-que-usuarios-linux-devem-se-preocupar-com-riscos-em-seguranca-e-o-que-pode-ser-feito-para-se-proteger.html)

### 5. Conceder permissão completa “para tudo e todos”

Depois que se aprende as **permissões em sistema de arquivos Linux**, parece que
o descuido aumenta. Quem nunca teve um problema e encontrou na internet como
solução sendo “problema de permissão”? Daí, você concede a famosa permissão
“777” :/

Primeiro, não existe “problema de permissão”. **O controle de acesso via
permissões é uma solução**. O que acontece é o uso das permissões erradas no
arquivo, em questão. Por isso, o correto é encontrar permissões adequadas para
aquele arquivo ou pasta.

Existem permissões que deve ser concedidas somente para o dono do arquivo.
Outras para o grupo e outros, e permissões somente de execução e não de escrita.
Cada nuance dessas [põe em risco a segurança do seu
sistema](https://www.linuxdescomplicado.com.br/2017/02/por-que-usuarios-linux-devem-se-preocupar-com-riscos-em-seguranca-e-o-que-pode-ser-feito-para-se-proteger.html),
principalmente se feito em um recurso protegido pelo modo super-usuário :/

*****

> **Publicado originalmente em:
> **[https://www.linuxdescomplicado.com.br/2019/08/erros-que-todo-usuario-linux-cometeu-ao-comecar-aprender-linux.html](https://www.linuxdescomplicado.com.br/2019/08/erros-que-todo-usuario-linux-cometeu-ao-comecar-aprender-linux.html)

