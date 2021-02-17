--- 
draft: false
date: 2021-02-17T15:00:38-03:00
title: "Boas práticas para deixar seu servidor Linux mais seguro pós instalação"
subtitle: "Não basta instalar"
description: "Depois de instalar um servidor Linux é preciso seguir algumas ações para aumentar sua segurança"
summary: ""
slug: "servidor-linux-mais-seguro-apos-instalacao"
featured_image: ""
keywords:
 - sudo
 - pam
 - LUKS
 - fstab
 - ssh
images:
  - /2021/02/servidor-linux-mais-seguro-apos-instalacao/banner.jpeg
authors:
tags:
categories: 
 - Linux
externalLink: ""
series:
---

Nenhum sistema é 100% seguro… fato! O Linux não seria exceção dessa regra. 
Ameaças externas ao sistema sempre vão existir. 

Entretanto, o que deve ser dito é que os riscos que um usuário Linux corre são diferentes comparados a outros sistemas não Unix. 
Os riscos para um usuário Linux se concentram na maneira como ele usa e mantém o sistema. 

Portanto, seguem algumas recomendações importantes após ter instalado um Servidor Linux:

### 1 - Sempre, menos é mais

Ao instalar um servidor Linux, sempre existem pacotes que você pode não precisar no momento

Uma boa conduta é enxugar o máximo e deixar somente o essencial. Menos pacotes, logo menos vulnerabilidades

### 2 - Criptografia de partições

É uma opção que vem por padrão na instalação de qualquer sistema Linux, inclusive os desktops

Adicionar essa camada de segurança mantêm suas partições mais seguras na inicialização e durante as montagens

### 3 - Atributos de partições

O mínimo é formatar as partições. Mas, somente isso não basta! 

Atributos de montagens como, por exemplo, "não execução" e "somente leitura" são necessárias para evitar ações indesejadas

### 4 - Controle de acesso

Definir permissões é tarefa básica. Muitos serviços não funcionam, adequadamente, por má configuração nesse quesito

Mas, não se limite a elas. Lista de controles de acesso (ACL) fazem uma excelente casadinha com as permissões regulares

### 5 - Não basta usar o sudo

Usar o sudo é opcional. Se decidiu por ele, configure-o!

Nessa conf você pode definir usuários/grupos e permissões granulares para executar como sudo. Use e abuse disso!

### 6 - Pú, pá, PUM... PAM

O módulo plugável de autenticação (PAM) é responsável por centralizar os recursos de autenticação, contabilidade e autorização do sistema

Restrições de logins, complexidade de senhas, bloqueios e muitas outros!

#### 7 - Crie seu par de chaves

Acesso remoto apenas por senha é vacilo. Usar par de chaves pública e privada é lei!

Então, obrigatoriamente, crie seu par de chaves RSA e salve no seu chaveiro virtual. Configure o serviço SSH e sucesso!
