# Gogs - Open Source Self-Hosted Git Server

## Gogs - Introdução
O Gogs é uma ferramenta Open Source de serviço de *Git* (um dos vários tipos de *VCS - Version Control System* existentes) que foi criada com o intuito de ser uma opção de fácil utilização, instalação, manutenção, leve, *cross-platform* e *self-hosted*. Criado com a linguagem de programação Go da Google sua sigla vem de
**Go** **G**it **S**ervice - Gogs.

Por ter sido feito em Go e devido a linguagem ser de distribuição em multiplataformas (e devido a binários independentes), o Gogs consegue funcionar em qualquer sistema que consiga compilar Go, entre eles: Linux, Windows, Mac OS X e ARM, sendo este um diferencial do Gogs.

### Self-Hosted
O *Self-Hosted* significa ter um serviço ou sistema no qual o administrador tem controle total sobre a ferramenta, devido a sua hospedagem ser feita em uma máquina que está em posse do administrador, conseguindo então gerenciar a instalação, execução e demais tarefas envolvidas, além de ter controle nos arquivos, nos usuários, níveis de segurança, permissões, entre outros. Mas fica em responsabilidade do administrador, também, toda a manutenção, eventuais updates e problemas que possam surgir durante o uso do serviço, para tal o Gogs oferece um fórum para usuários.

## Vantagens
- Total controle sobre o serviço
- Privacidade
- Segurança
- Independência
- Gratuidade
- Portabilidade
- Facilidades (Flexibilidade)
- Integração

## Desvantagens
- Custo
- Manutenção

## Instalação
O Gogs, como os seus desenvolvedores o anunciam, é um sistema de fácil instalação e nesse tutorial vamos ensinar como você pode instalar e ter um servidor git Gogs rodando em sua máquina para os mais diversos projetos.

### Requerimentos de Hardware
 - Um Raspberry Pi ou um Droplet do Digital Ocean já tem o que é necessário para que você consiga rodar sua instância do Gogs. Há como também rodar em uma Docker de 64MB como um CaaS (Container as a Service - https://blog.docker.com/2016/02/containers-as-a-service-caas/)
 - Uma CPU dual-core com 512MB de RAM é o mínimo para uma instância que será utilizada por times.
 - CPUs com mais cores são necessárias quando o time que usufruirá da instância for grande, entretanto o uso de RAM permanece baixo.

### Pré-requisistos
 - Banco de Dados

###### Referências
 - https://gogs.io/docs
 - https://github.com/gogits/gogs
 - https://git-scm.com/doc
 - https://golang.org/doc/
 - https://opensource.org/
 - https://pt.wikipedia.org/wiki/Sistema_de_controle_de_vers%C3%B5es
 - https://fjorgemota.com/gogs-um-sistema-versatil-para-hospedagem-de-repositorios-git/
