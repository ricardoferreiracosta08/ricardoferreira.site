---
draft: false
date: 2020-11-10T13:24:58-03:00
title: "Aplicação web em arquitetura de microserviço utilizando Docker 🐳"
subtitle: "Ou Docker ou racha"
description: "Aplicação web PHP em arquitetura de microserviço com containers Docker que se conecta via API Restful"
slug: "aplicacao-web-microservico-docker-python-php"
keywords:
 - docker
 - microserviço
 - linux
 - python
 - php
 - flask
 - api
 - restful
 - sqlalchemy
 - postgresql
featured_image: ""
images:
  - /2020/11/aplicacao-web-microservico-docker-python-php/overview.png
authors:
tags:
categories:
  - Docker
externalLink: ""
series:
---

Tendo em vista a **Metodologia "The Twelve-Factor App"**, criada por Adam Wiggins, co-fundador da PaaS [Heroku](https://www.heroku.com/), 
que preconiza todo software cloud entregue como serviço deve seguir algumas premissas de desenvolvimento que **impulsonam o uso da arquitetura
de Microserviços**, eu apresento uma solução web simples que demonstra na prática o emprego de todos os 12 fatores da Metodologia!

## Por que Microserviço? 🤨

Microserviço é um conceito que garante que uma aplicação **possa ser dividida** em múltiplos serviços menores (microserviços) que se 
comunicam entre si, tradicionalmente, via APIs Rest (métodos GET/POST/PUT/DELETE do protocolo HTTP + JSON).

As **principais vantagens** são:

+ Cada microserviço é independente garantindo **baixo acoplamento** e possui responsabilidade única garantindo **alta coesão** 
melhorando a manutenção do código e **reuso do software**
+ Desse modo os **pontos de falhas** tendem a serem isolodados mais facilmente gatarantido a resilência do software. Por outro lado, aumentam-se 
os pontos de falhas que exigem maior esforço no monitoramento para a mitigação efeciente das falhas
+ Modelagem com base em **conceitos de negócio** (Domain-Driven Design) evitando uma modelagem falha e baseada puramente em aspectos técnicos
+ **Autonomia e indepedência** exigem automação no deploy que facilitam a implementação de técnicas de CI/CD vistas no DevOps
+ Cada microserviço pode ter sua **própria linguaguem de desenvolvimento**, databases e ferramentas
+ Tudo passa a ser orientado por eventos e mensagens entre as partes
+ Totalmente aplicável a **escalonar horizontalmente** seu software. Aqui encaixa-se o uso de orquestradores de containers, como Swarm e Kubernetes

[FORM_CONVERTKIT]

Tudo isso confronta com as **práticas tradicionais de desenvolvimento** que estabelecem um único ponto (famoso monólito) de criação. 
Dificultando a manutenção, concentrando as falhas e diminuindo a resiliência já que a aplicação precisará parar ou reiniciar, por completo caso o 
módulo de upload precise de atualizaçaõ ou tenha dado problema, por exemplo.

## Qual é dessa Metodologia aí? 🤔

Ela sintetiza, em 12 fatores, **boas práticas de desenvolvimento** de aplicação web. Ela é, altamente, recomendada para qualquer 
Desenvolvedor que esteja construindo aplicações que rodam como serviço e Engenheiros de Operações que implantam ou administram tais 
aplicações! Recomendações do próprio autor.

Estes fatores são realmente um ótimo 'guideline' para direcionar a melhor maneira para construir uma aplicação baseada em microserviço, pois 
oferecem maneiras para garantir os **principais pilares dos microserviços**, tais como: independência, resiliência, autonomia, descentralização
e escalabilidade.

Sendo assim, os [12 fatores](https://12factor.net/pt_br/) são:

1. **Base de Código** “Codebase”
> Uma base de código com rastreamento utilizando controle de revisão
2. **Dependências** “Dependencies”
> Declare e isole as dependências
3. **Configurações** “Config”
> Armazene as configurações no ambiente
4. **Serviços de Apoio** “Backing Services”
> Trate os serviços de apoio, como recursos ligados
5. **Construa, lance, execute** “Build, Run, Release”
> Separe estritamente os builds e execute em estágios
6. **Processos** “Stateless Processes”
> Execute a aplicação como um ou mais processos que não armazenam estado
7. **Vínculo de porta** “Port Binding”: 
> Exporte serviços por ligação de porta
8. **Concorrência** "Concurrency"
> Dimensione por um modelo de processo
9. **Descartabilidade** "Disposability"
> Maximizar a robustez com inicialização e desligamento rápido
10. **Dev/prod semelhantes** "Dev-Prod Parity"
> Mantenha o desenvolvimento, teste, produção o mais semelhante possível
11. **Logs** 
> Trate logs como fluxo de eventos
12. **Processos de Admin** "Admin Processes"
> Executar tarefas de administração/gerenciamento como processos pontuais

## Veja na prática! 🤘

Visão geral do projeto:

![](./overview.png)

**Tecnicamente**, é uma aplicação web PHP em arquitetura de microserviço com **containers Docker** que se conecta via API Restful 
Flask com mapeamento objeto-relacional SQLAlchemy, escrito em Python, com persistência em banco de dados PostgreSQL. 

A fim de garantir que você tenha uma maior absorção do que está sendo apresentado aqui, acesse o [código completo desse projeto no meu GitHub](https://github.com/ricardoferreiracosta08/microservice-simple-docker-compose) e acompanhe em detalhes como cada trecho e 
recurso foi adotado tendo como base a Metodologia discutida anteriormente.

**Leia o Readme** para proceder com a execução e veja na prática seu funcionamento!

{{< alert success no-icon >}}
Esse artigo foi criado por conta da aula "Microserviço na prática - aplicação web PHP simples conectada via API Restful" apresentado no meu curso de Introdução a Docker! Curtiu? 
[Eu quero o curso](http://bit.ly/cursoAprendaDockerdoZero)
{{< /alert >}}

{{< alert danger no-icon >}}
O escopo aqui não é provisionamento e orquestração da aplicação, apenas apresentar práticas de 
desenvolvimento em microserviços usando containers Docker. Por isso, não abordo as diferentes etapas de desenvolvimento!
{{< /alert >}}

#### 1. Base de Código "Codebase"
Esteja sempre centrado no versionamento do código, em diferentes etapas do desenvolvimento integrado e continuado 
(development, staging, production, etc) e ciente de que existe apenas uma base de código por aplicação, mas existirão vários deploys da mesma. 

Acesse toda a base de código desse projeto no meu GitHub [aqui](https://github.com/ricardoferreiracosta08/microservice-simple-docker-compose)!

#### 2. Dependências "Dependencies"

No projeto, eu uso o arquivo requirements.txt que usa o gerenciador de pacotes pip3 e o virtualenv do Python. 
Isso mantém declarada e isolada explicitamente, respectivamente, todas as dependências, e suas versões, do projeto. 

Os services API mantêm essa característica.

{{< highlight bash "linenos=inline,linenostart=1,style=dracula" >}}
flask==1.0.2
flask-sqlalchemy==2.3.0
psycopg2==2.8.4
{{< /highlight >}}

#### 3. Configurações "Config"

Mantenha todas as configurações do ambiente declaradas "fora do código". Isso auxilia a administração entre os diversos tipos 
de etapas do desenvolvimento. Evite armazenar as configurações no código como constantes, por exemplo: variáveis de conexão com banco de dados. 
Pois, esse 4º fator exige uma estrita separação entre configuração e código!

Tendo isso em vista, é possível observar que eu uso os arquivos de configuração de conexão com o banco PostgreSQL explícitos nos arquivos 
database.conf em todos os services que persistem dados. Inclusive, elas são passadas como variáveis de ambiente (ENVs) no docker-compose.yml:

{{< highlight bash "style=dracula" >}}
POSTGRES_USER=test
POSTGRES_PASSWORD=password
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
POSTGRES_DB=books
{{< /highlight >}}

{{< highlight yaml "linenos=inline,lines=inline,hl_lines=5,linenostart=1,style=dracula" >}}
version: '3.5'
services:
  database-books:
    image: postgres:13-alpine
    env_file: db-books/database.conf
    volumes:
      - db_volume-books:/var/lib/postgresql/data
#rest of code
{{< /highlight >}}

#### 4. Serviços de Apoio "Backing Services"

A fim de garantir boa portabilidade e fácil manutenção, trate serviços de apoio, como persistência de dados,
mensageria e envio de e-mails, como um "recurso anexado" que facilmente pode ser alterado e não causar grandes impactos ou mudanças de código. 
Tudo isso garante baixo acoplamento ao deploy!

Sendo assim, no meu caso, atráves do docker-compose, eu consigo anexar e desanexar facilmente os recursos de containers de persistência de dados. 
No caso o service do PostgreSQL. Inclusive, posso alterar de versão ou indicar outro volume de dados que nenhuma mudança de código é exigida:

{{< highlight yaml "linenos=inline,lines=inline,hl_lines=4 7,linenostart=1,style=dracula" >}}
version: '3.5'
services:
  database-books:
    image: postgres:13-alpine
    env_file: db-books/database.conf
    volumes:
      - db_volume-books:/var/lib/postgresql/data
#rest of code
{{< /highlight >}}


#### 5. Construa, lance, execute "Build, Run, Release"

Esse fator reforça as etapas do desenvolvimento moderno conhecidos como Build, Release e Run stages. Inclusive, automação de deploy.

Mesmo não sendo escopo do meu projeto, tenho uma base de código (fator 1) que é pré-requisito para esse critério! Veja mais sobre
[aqui](https://12factor.net/pt_br/build-release-run)

#### 6. Processos "Stateless Processes"

Esse fator está no "core" da arquitetura de microserviços. Ela preconiza que você não deve salvar estado em seus serviços, pois aplicações
devem executar como um único processo sem armazenar estado. Isso garante a alta coesão e mantém a responsabilidade única!

"Sem armazenar estado" está relacionado com a persistência dos dados dos microserviços. No caso de containers Dockers isso é primordial, pois 
containers são voláteis e não armazenam estado (pegou a ideia?). Logo, precisa usar um serviço de apoio stateful (que armazena o seu estado), 
tipicamente uma base de dados.

No meu caso, simplesmente o fato de ter um container PostgreSQL não garante esse fator. Para tal, foi preciso criar um objeto Docker volume para 
persistir todos os dados de banco:

{{< highlight yaml "linenos=inline,lines=inline,hl_lines=1,linenostart=9,style=dracula" >}}
    volumes:
       - db_volume-books:/var/lib/postgresql/data
#rest of code
{{< /highlight >}}

#### 7. Vínculo de Portas "Port Binding"

De acordo com esse fator, a aplicação web deve exportar requisição HTTP como um serviço através da vinculação a uma porta 
e escutar as requisições que chegam na mesma. Dessa maneira, ao vincular portas, um serviço pode se tornar apoio para um outro serviços, 
provendo a URL do microserviço como um identificador de recurso na configuração do microserviço consumidor.

No meu caso, no microserviço web, no arquivo index.php, eu tive que informar a URL e porta do microserviço da API Restful Flask 
para ele "consumir" as requisições de saída exibindo os dados na web:

{{< highlight php "linenos=inline,lines=inline,hl_lines=2,linenostart=1,style=dracula" >}}
<?php
$_ENV['URL_API_BOOKS'] = "http://microservice_api-books_1:5000/";
$_ENV['URL_API_READERS'] = "http://microservice_api-readers_1:5000/";
?>
{{< /highlight >}}

{{< highlight php "linenos=inline,hl_lines=1,linenostart=9,style=dracula" >}}
    $json = file_get_contents($_ENV['URL_API_BOOKS']);
{{< /highlight >}}

#### 8. Concorrência "Concurrency"

Aplicações web necessitam ser escaláveis horizontalmente. Logo, elas podem ter 1 ou mais instâncias de seus microserviços sendo executadas,
simultaneamente. Isso aumenta a disponbilidade e concorrência dos processos. 

Como eu estou trabalhando com o docker-compose, ele, por padrão, prepara para um ambiente escalável que pode ser orquestrado no Dokcer Swarm,
Kubernetes ou outros. Inclusive, ele sufixa todos os services com numerações de 1 a quantidade de réplicas criadas:

{{< highlight bash "style=dracula" >}}
             Name                           Command               State           Ports         
------------------------------------------------------------------------------------------------
microservice_api-books_1          /usr/src/app/entrypoint.sh       Up      0.0.0.0:5000->5000/tcp
microservice_api-readers_1        /usr/src/app/entrypoint.sh       Up      0.0.0.0:5001->5000/tcp
microservice_database-books_1     docker-entrypoint.sh postgres    Up      5432/tcp              
microservice_database-readers_1   docker-entrypoint.sh postgres    Up      5432/tcp              
microservice_web_1                docker-php-entrypoint apac ...   Up      0.0.0.0:80->80/tcp
{{< /highlight >}}

#### 9. Descartabilidade "Disposability"

De acordo com esse fator, todas as instâncias de microserviços devem ser "descartavéis" para iniciar e parar suas execuções rapidamente e sem maiores
complicações, a qualquer tempo. Mais um motivo dos quais eles devem ser stateless (fator 6). Isso facilita o escalonamento rápido.

A própria natureza de containers garanti isso!

#### 10. Dev/prod semelhantes "Dev-Prod Parity"

Manter todas as etapas do desenvolvimento (development, staging,production, etc) mais semalhantes o possível é meta desse fator. 
Entrega e Desenvolvimento contínuos (CD) dependem de uma Integração contínua (CI). Um time de DevOps tende a priorizar por isso. 

Mais, uma vez, o uso de containers, por conta de sua padronização de ambientes em pacotes de imagens, ajuda muito nesse sentido!
Viva os containers 😂

{{< alert success no-icon >}}
Quer aprender a utilizar e administrar containers Docker? Tenho um curso do zero para você! 
[Eu quero o curso agora](http://bit.ly/cursoAprendaDockerdoZero)
{{< /alert >}}

Alternativamente, ferramentas de provisionamento declarativo tais como Chef e Puppet combinado com ambientes virtuais leves como 
Vagrant também permitem desenvolvedores rodar ambientes locais que são bem próximos dos ambientes de produção.

#### 11. Logs

Logs fazem parte do pacote do monitoramento, tão primordial no universo dos microserviços.
Além disso, logs são imprescindíveis para debugar e verificar a saúde da aplicação. A partir disso, os logs não devem ser armazenados em 
um storage central, mas sim tratados como fluxos de eventos contínuos que devem capturados e armazenados em service separado.

No meu cenário simples tenho clareza e acesso aos logs direto da CLI do docker compose. No caso o "docker-compose logs":

{{< highlight bash "style=dracula" >}}
web_1   | 192.168.160.1 - - [11/Nov/2020:14:13:17 +0000] "GET / HTTP/1.1" 200 401 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.111 Safari/537.36"
web_1   | 192.168.160.1 - - [11/Nov/2020:14:13:18 +0000] "GET /favicon.ico HTTP/1.1" 404 487 "http://localhost/" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.111 Safari/537.36"
api_1       |  * Serving Flask app "api.py"
api_1       |  * Environment: production
database_1  | 2020-11-11 16:25:37.316 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
database_1  | 2020-11-11 16:25:37.316 UTC [1] LOG:  listening on IPv6 address "::", port 5432
{{< /highlight >}}

#### 12. Processos de Admin "Admin Processes"

Execute tarefas de administração/gerenciamento como processos únicos - tarefas como migração de banco de dados ou execução de scripts únicos 
no ambiente. O objetivo é separar da execução do processo do microserviço de um processo de administração como uma consulta ou update de banco, 
por exemplo.

No meu caso, eu uso a própria CLI do docker-compose que garante uma execução multiplexada do processo vigente. Isso é a natureza dos containers
Docker:

{{< highlight bash "style=dracula" >}}
docker-compose exec database-books psql -U test -p 5432 -d books
{{< /highlight >}}

## Referências

+ [Curso Docker do Zero - Introdução a administração de containers](http://bit.ly/cursoAprendaDockerdoZero)
+ [GitHub desse projeto](https://github.com/ricardoferreiracosta08/microservice-simple-docker-compose)
+ [The Twelve-Factor App (pt_BR)](https://12factor.net/pt_br/)
+ [The Twelve-Factor App — A Successful Microservices Guideline](https://dev.to/simon_sugob/the-twelve-factor-appa-successful-microservices-guideline-3a1h)
+ [Book "Building Microservices"](https://samnewman.io/books/building_microservices/)
+ [Microservice Architecture](https://microservices.io/)
+ [The Twelve-Factor App — A Successful Microservices Guideline](https://dev.to/simon_sugob/the-twelve-factor-appa-successful-microservices-guideline-3a1h)
+ [Simple App with Flask, SQLAlchemy and Docker](https://medium.com/@hmajid2301/implementing-sqlalchemy-with-docker-cb223a8296de)
+ [An example of a RESTful API Deployed on a Docker Container](https://github.com/SwarnimWalavalkar/rest-api-microservice-docker)
+ [DOCKER COMPOSE WITH TWO CONTAINERS - FLASK REST API SERVICE CONTAINER AND AN APACHE SERVER CONTAINER](https://www.bogotobogo.com/DevOps/Docker/Docker-Compose-FlaskREST-Service-Container-and-Apache-Container.php)
+ [Python REST APIs With Flask, Connexion, and SQLAlchemy – Part 2](https://realpython.com/flask-connexion-rest-api-part-2/)
