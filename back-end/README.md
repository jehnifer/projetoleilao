#BACK-END SISTEMA LEILÃO

##O PROJETO DEVE RODAR NA PORTA 8080 PARA AS REQUISIÇÕES DO FRONT-END

###Tecnologias utilizadas
	Spring-Boot (Web, JPA, Validation, Devtools)
	Banco de Dados (Hibernate, PostgreSQL)
	Lombok
	
###Funções do sistemas
	Cadastro de Participantes
		Validação de campos(vazio e tamanho)
	Cadastro de Leilões
		Validação de campos(vazio e tamanho)
		Um leilão é inativo quando é cadastrado no sistema
		Um leilão expira quando passa da sua data de fechamento.
	Cadastro de Lances
		Um mesmo participante não pode dar dois lances seguidos no mesmo leilão.
		O valor do lance inicial deve ser maior que o valor estipulado pelo leilão
		Um lance não pode ser menor que o último lance já cadastrado