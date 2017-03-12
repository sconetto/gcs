# Gogs - Open Source Self-Hosted Git Server

## Gogs - Introdução
O Gogs é uma ferramenta Open Source de serviço de *Git* (um dos vários tipos de *VCS - Version Control System* existentes) que foi criada com o intuito de ser uma opção de fácil utilização, instalação, manutenção, leve, *cross-platform* e *self-hosted*. Criado com a linguagem de programação Go da Google sua sigla vem de **Go** **G**it **S**ervice - Gogs.

Por ter sido feito em Go e devido a linguagem ser de distribuição em multiplataformas (e devido a binários independentes), o Gogs consegue funcionar em qualquer sistema que consiga compilar Go, entre eles: Linux, Windows, Mac OS X e ARM, sendo este um diferencial do Gogs.

### Self-Hosted
O *Self-Hosted* significa ter um serviço ou sistema no qual o administrador tem controle total sobre a ferramenta, devido a sua hospedagem ser feita em uma máquina que está em posse do administrador, conseguindo então gerenciar a instalação, execução e demais tarefas envolvidas, além de ter controle nos arquivos, nos usuários, níveis de segurança, permissões, entre outros. Mas fica em responsabilidade do administrador, também, toda a manutenção, eventuais updates e problemas que possam surgir durante o uso do serviço, para tal o Gogs oferece um fórum para usuários.

## Vantagens
- Total controle sobre o serviço
- Privacidade - controle da base de usuários e possibilidade de repositório de privados;
- Segurança - realizar o controle de papéis de um usuário dentro de um repositório;
- Independência - esse é um quesito importante, já que o serviço independe de internet, por exemplo, para estar disponível;
- Gratuidade de Software - escrita na linguagem de programação de código aberto Go, da Google, esse serviço é gratuito;
- Portabilidade/Multiplataforma - o Gogs roda em Linux, Windows e Mac;
- Facilidades (Flexibilidade) - * 
- Integração - possibilidade de integração com alguns outros serviços (por exemplo, WebHook para integração de Slack ou para envio de e-mail). O Gogs também fornece integração com alguns projetos facilmente, como o Taiga.io, por exemplo, facilitando e muito o seu workflow;

## Desvantagens
- Custo de Hardware - para a hospedagem do serviço é necessário um servidor. Para isso há o custo de uma máquina física ou virtual;
- Manutenção - atualizações e upgrades são feitos manualmente tendo que ser parado o serviço.

## Instalação
O Gogs, como os seus desenvolvedores o anunciam, é um sistema de fácil instalação e nesse tutorial vamos ensinar como você pode instalar e ter um servidor git Gogs rodando em sua máquina para os mais diversos projetos.

### Requerimentos de Hardware
 - Um Raspberry Pi ou um Droplet do Digital Ocean já tem o que é necessário para que você consiga rodar sua instância do Gogs. Há como também rodar em uma Docker de 64MB como um [CaaS](https://blog.docker.com/2016/02/containers-as-a-service-caas/) (Container as a Service)
 - Uma CPU dual-core com 512MB de RAM é o mínimo para uma instância que será utilizada por times.
 - CPUs com mais cores são necessárias quando o time que usufruirá da instância for grande, entretanto o uso de RAM permanece baixo.

### Pré-requisistos
 - Banco de Dados (Necessário escolher um dos listados abaixo):
 	+ [MySQL](https://www.mysql.com/downloads/): Versão >= 5.5.3
 	+ [PostgreSQL](https://www.postgresql.org/download/)
 	+ [MSSQL](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
 	+ [TiDB](https://github.com/pingcap/tidb) (Experimental, conexão via protocolo MySQL)
 	+ ou **Nenhum** com SQLite3
 	+ **LEMBRE-SE**: Use `scripts/mysql.sql` para criar um database chamado `gogs` (*default*). Se você criá-lo manualmente certifique-se que o encoding é `utf8mb4`.
 - [Git](https://git-scm.com/downloads) (bash)
   + Versão >= 1.7.1 para ambos servidor e cliente
   + No Windows é recomendado sempre a última Versão
 - Servidor SSH funcional
   + **Ignore se você for usar apenas o protocolo HTTP/HTTPS ou se irá usar o *builtin SSH Server* (Servidor SSH pré-instalado)**
   + É recomendado o [Cygwin OpenSSH](http://docs.oracle.com/cd/E24628_01/install.121/e22624/preinstall_req_cygwin_ssh.htm#EMBSC150) ou [Copssh](https://www.itefix.net/copssh) no Windows

Há 5 formas de instalar o Gogs:
 - [Instalar pelos binários](https://gogs.io/docs/installation/install_from_binary.html)
 - [Instalar pela *source*](https://gogs.io/docs/installation/install_from_source.html)
 - [Instalar por pacotes](https://gogs.io/docs/installation/install_from_packages.html)
 - [Instalar com o Vagrant](https://github.com/geerlingguy/ansible-vagrant-examples/tree/master/gogs)
 - [Instalar em um Container Docker](https://github.com/gogits/gogs/tree/master/docker)

### Instalando em um Container Docker
Esta é uma das maneiras mais fáceis de instalar o Gogs mas antes de seguir para instalação certifique-se de ter o *Docker* instalado em sua máquina. A seguir como instalar em uma máquina linux Ubuntu:

1. Instale os seguintes pacotes para permitir ao `apt` usar repositórios sobre o protocolo HTTPS:
```sh
$ sudo apt-get install apt-transport-https
$ sudo apt-get install ca-certificates
$ sudo apt-get install curl
$ sudo apt-get install software-properties-common
```

2. Adicione a chave GPG oficial do Docker
```sh
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
Verifique que o *fingerprint* da chave é `9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88`.
```sh
$ sudo apt-key fingerprint 0EBFCD88
pub   4096R/0EBFCD88 2017-02-22
Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid             Docker Release (CE deb) <docker@docker.com>
sub   4096R/F273FCD8 2017-02-22
```
**`ATENÇÃO`**: O *fingerprint* da chave pode mudar devido a atualizações, sempre verique [aqui](https://docs.docker.com/engine/installation/linux/ubuntu/#install-using-the-repository) sua chave.

3. Use o seguinte comando para configurar o repositório da versão *stable* (estável):
```sh
$ sudo add-apt-repository \
  "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
**`ATENÇÃO`**: certifique-se da sua arquitetura, no exemplo acima o repositório adicionado está atrelado a arquitetura *64 bits*.

4. Atualize o índice de pacotes do `apt` e por fim instale o Docker
```sh
$ sudo apt-get update
$ sudo apt-get install docker docker.io
```

5. Depois de instalado a Docker é preciso baixar o Gogs, é possível baixar a última versão estável do Gogs pela Docker (recomendado), basta rodar o simples comando
```sh
docker pull gogs/gogs
```
Caso você tenha baixado o projeto direto pelo Github do Gogs será preciso criar o container e executar os binários descompactados.

6. Após o termino do *download* da imagem do Gogs para Docker execute o seguinte comando para rodar o container:
```sh
docker run -d --name=gogs -p 10022:22 -p 10080:3000 -v /var/gogs:/data gogs/gogs
```

7. O Gogs já está executando, agora basta acessar o endereço **http://127.0.0.1:10080/** ou **http://localhost:10080/**, nesse primeiro momneto será solicitado a configuração do repositório, no *Tipo de Banco de Dados* configure o SQLite, é a forma mais simples e a que vamos usar nesse tutorial, mude o endereço do campo *URL do Aplicativo* de **http://localhost:3000/** para **http://127.0.0.1:10080/** e o campo *Porta SSH* de **22** para **10022**. Agora basta clicar no fim da página em **Instalar Gogs** para finalizar as configurações.

**OBS**: Caso queira modificar alguma configuração do gogs procure a pasta `custom/conf/app.ini` as configurações ficam neste arquivo `app.ini`, neste [link](https://gogs.io/docs/advanced/configuration_cheat_sheet) você consegue ver como configurar seu Gogs.

9. Agora, com o Gogs configurado, é preciso criar uma conta de usuário, que será assumida automaticamente pelo Gogs como uma conta de **administrador**. Acesse **http://127.0.0.1:10080/user/sign_up** e crie um usuário com senha e e-mail, confirme a senha e o captcha solicitado. Após criada a conta do administrador o Gogs te redirecionará para a página de login, insira os dados e o Gogs te redirecionará para a sua *dashboard*. Pronto, seu Gogs já está configurado e executando, basta usá-lo!

### Instalando pelos binários 
Outra forma de realizar a instalação do Gogos através de binário. A seguir como instalar em uma máquina linux Ubuntu:

1. Antes de iniciar, certifique-se que já tenha um descompactador instalado (exemplo, unzip)
```sh
$ sudo apt-get install unzip
```

2. Faça o download do arquivo (a versão utilizada para esse tutorial foi a v0.10.8 para SO Linux 64 bits)
```sh
$ wget https://dl.gogs.io/0.10.8/linux_amd64.zip
```

3. Realize a descompactação do arquivo
```sh
$ unzip linux_amd64.zip
```

4. Acesse a pasta que foi descompactada (nesse caso chamada de gogs/)
```sh
$ cd gogs/
```

5. Para execução do Gogs rode o comando
```sh
$ ./gogs web
```

6. Pronto! A partir de agora o Gogs já está sendo executado. Para realizar a primeira configuração basta acessar **http://0.0.0.0:3000**.

###### Referências
 - https://gogs.io/docs
 - https://github.com/gogits/gogs
 - https://git-scm.com/doc
 - https://golang.org/doc/
 - https://opensource.org/
 - https://pt.wikipedia.org/wiki/Sistema_de_controle_de_vers%C3%B5es
 - https://fjorgemota.com/gogs-um-sistema-versatil-para-hospedagem-de-repositorios-git/
