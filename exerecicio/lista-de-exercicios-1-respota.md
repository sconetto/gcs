GCS - Gerência de Configuração de Software
UnB/FGA - Universidade de Brasília
Professor: Renato Coral / Matheus de Sousa Faria
Aluno: João Pedro Sconetto
Matrícula: 14/0145940

1) Itens de configuração:
	É um elemento unitário que será gerenciado, ou seja, um item que precisará sofre controle de versões e de mudanças. Exemplos:
	* Um arquivo de código fonte;
	* Um documento de texto;
	* Um CD de instalação de sistema operacional;

   Baselines:
	É um marco de referência no desenvolvimento de software, que é caracterizado plea entrega de um ou mais itens de configuração (em inglês, Software Configuration Items - SCIs) e pela aprovação desses SCIs, obtida por meio de uma revisão técnica formal, segundo PRESSMAN no contexto de engenharia de software. Exemplos:
	* Versão 1.0;
	* Versão de correção de erros 1.1;
	* Versão personalizada para o sistema do governo americano;

2) Representa todo o trabalho envolvido no gerenciamento, no contexto de engenharia de software, do ambiente a qual vai ser desenvolvido o software, tratando de gerenciar todos os elementos envolvidos (neste contexto de configuração de software são tratados apenas aqueles que se encontram em formato eletrônico) que fazem parte de dada configuração.

3) Comando para clonar um repositório (partindo do príncipio que se está trabalhando com repositórios Git):
git clone <link-para-o-repositorio>

Comando para commitar uma mudança (partindo de que os arquivos que foram modificados já foram adicionados para commitar):
git commit -m "<mensagem-de-commit>" (o comando '-m' indica que a mensagem será escrita na própria linha do comando, caso não tenha o '-m' será aberto o editor setado como padrão do git para que possa ser inserido a <mensagem-de-commit>)

Comando para atualizar o repositório remoto:
git push <nome-do-remote-do-repositório> <nome-da-branch> (assim será enviado todas a modificações para o repositório na branch explicitada)

4) Um sistema de controle de versões (ou versionando), VCS (singla do inglês version control system) ou ainda SCM (sigla também do inglês source code management), é um software com a finalidade de gerenciar diferentes versões de quaisquer arquivos em desenvolvimento. Os mais comuns, que também são soluções livre, são:
* Mercurial
* Git
* SVN

5) Como Explicitado na questão anterior, se trata de um software que tem a finalidade de gerenciar as diferentes versões de quaisquer arquivos em desenvolvimento.
