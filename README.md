# Instalando o Pentaho BI Server, CTools e Saiku no Ubuntu

## O que é o Pentaho?

Pentaho é um software de código aberto para inteligência empresarial, desenvolvido em Java. A solução cobre as àreas de ETL, reporting, OLAP e mineração de dados (data-mining). Desenvolvido desde 2004 pela Pentaho Corporation o software foi considerado uma das melhores aplicações para inteligência empresarial em 2008 pela InfoWorld. Fonte: [Wikipédia Pentaho](http://pt.wikipedia.org/wiki/Pentaho "Wikipédia Pentaho").

## Criando um usuário e grupo Pentaho

Abra o terminal (ctrl+alt+t) e execute os seguintes comandos:

`sudo addgroup pentaho`

`sudo adduser --system --ingroup pentaho --disabled-login pentaho`

## Instalando o JDK (Java)

**Link:** [Instale o Oracle Java (JDK) 7 no Ubuntu](http://www.ubuntudicas.com.br/blog/2012/04/instale-o-oracle-java-jdk-7-no-ubuntu-12-04-e-11-10/ "Instale o Oracle Java (JDK) 7 no Ubuntu").

## Instalando o Pentaho BI Server

Com o Java já instalado, podemos seguir com a instalação do Pentaho BI Server.

1. Faça o download da última versão instável do Pentaho BI Server **aqui:** [Download Pentaho BI Server](http://sourceforge.net/projects/pentaho/files/Business%20Intelligence%20Server/ "Download Pentaho BI Server").

2. Abra o terminal (ctrl+alt+t) e digite os seguitnes comandos:

`sudo mkdir /opt/pentaho`

**OBS:** *Acesse a pasta onde o Pentaho BI Server foi salvo quando você fez o download*.

`cd ~/Downloads`

`gunzip biserver-ce-x.x.x-stable.tar.gz`

`tar xf biserver-ce-x.x.x-stable.tar`

`sudo mv biserver-ce /opt/pentaho/biserver-ce-x.x.x`

`sudo mv administration-console /opt/pentaho/administration-console-ce-x.x.x`

`cd /opt/pentaho`

`sudo ln -s biserver-ce-x.x.x biserver-ce`

`sudo ln -s administration-console-ce-x.x.x administration-console`

`sudo chown -R pentaho:pentaho /opt/pentaho`

## Iniciando o Servidor Pentaho

Abra o terminal (ctrl+alt+t) e digite os seguitnes comandos:

`cd /opt/pentaho/biserver-ce`

`sudo -u pentaho ./start-pentaho.sh`

## Acessando o Pentaho para usuários

1. Abra seu navegador da web e digite [http://localhost:8080](http://localhost:8080 "localhost pentaho user").

2. Clique em **Evaluation Login** e escolha o tipo de usuário para fazer login.

## Acessando o Pentaho Administration Console

Abra o terminal (ctrl+alt+t) e digite os seguitnes comandos:

`cd /opt/pentaho/administration-console`

`sudo -u pentaho ./start-pac.sh`

1. Abra seu navegador da web e digite [http://localhost:8099](http://localhost:8099 "localhost pentaho administration console").
2. Digite para o **User Name** *admin*.
3. Digite para o **Password** *password*.
4. Clique em login.

## Parando o Servidor Pentaho

Abra o terminal (ctrl+alt+t) e digite os seguitnes comandos:

`cd /opt/pentaho/biserver-ce`

`sudo -u pentaho ./stop-pentaho.sh`

## Parando o Pentaho Administration Console

Abra o terminal (ctrl+alt+t) e digite os seguitnes comandos:

`cd /opt/pentaho/administration-console`

`sudo -u pentaho ./stop-pac.sh`

# Instalando CTools e Saiku

Faça o download no seguinte repositório:

**Link:** [CTools installer](https://github.com/pmalves/ctools-installer "CTools installer").

Abra o terminal (ctrl+alt+t) e digite os seguitnes comandos:

`./ctools-installer.sh -s solutionPath [-w pentahoWebapPath]`

*Exemplo:*

`./ctools-installer.sh -s /pentahoServer/biserver-ce/pentaho-solutions -w /pentahoServer/biserver-ce/tomcat/webapps/pentaho`

Escolha os pacotes que você deseja instalar.

--------------------------------------------------------------------------------------------------------------------------

Traduzido de:

* [Install Pentaho BI Server 4.5 on Ubuntu 12.04 LTS Desktop](http://akbarahmed.com/2012/05/24/install-pentaho-bi-server-4-5-on-ubuntu-12-04-lts-desktop"Install Pentaho BI Server 4.5 on Ubuntu 12.04 LTS Desktop").

* [Thread: Back to basics: Step by step Pentaho + Ctools installation](http://forums.pentaho.com/showthread.php?86683-Back-to-basics-Step-by-step-Pentaho-Ctools-installation "Thread: Back to basics: Step by step Pentaho + Ctools installation").
