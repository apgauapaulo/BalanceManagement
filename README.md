# BalanceManagement

Instruções para testar aplicação Balance Management desenvolvida em Rust e MongoDB

Observação: Projeto em json em anexo (BalanceManagement.postman_collection.json)

1)	Adicionar conta com saldo inicial
Utilizar método Add do projeto;
Utilizar url localhost:4001/add
No body, passar os parâmetros:
“account_name” – Nome da conta (Exemplo: “Account2”)
“balance” – Saldo inicial da conta (Exemplo: 1000)
Será criado e retornado o OID da conta (Copiar oid para utilizar nos outros métodos)
 
2)	Consultar saldo
Utilizar método GetBy do projeto;
Utilizar url localhost:4001/get-by/oid (Oid gerado no método de adição);
Será retornado o oid, o nome (account_name) e o saldo (balance) da conta;
 
3)	Foi criado um método para facilitar os testes e visualizar todas as contas criadas e todos as movimentações
Utilizar método GetAll do projeto;
Utilizar url localhost:4001/get-all
Será retornado lista com todas as movimentações e contas criadas, bem como todos os seus dados.

4)	Método para realizar operações de débito e crédito
Utilizar método UpdateOperation do projeto;
Utilizar url localhost:4001/update-operation/oid (Oid gerado no método de adição);
- Para realizar operações de débito, deve passar os seguintes parâmetros:
“operation”: “debit”
“value” – valor a ser debitado (Exemplo 500)
 
- Para realizar operações de crédito, deve passar os seguintes parâmetros:
“operation”: “credit”
“value” – valor a ser creditado (Exemplo 500)
 
O resultado de ambas as operações será 1, caso funcione corretamente.
Após a utilização, poderá ser chamado o método de consulta de saldo para verificar atualização do saldo

5)	Consulta de extrato por datas
Utilizar método GetByDates do projeto;
Utilizar url localhost:4001/get-by-dates/Account2 (Nome da conta gerada no método de adição, também pode ser consultada nos métodos GetBy e GetAll);
Em body, utilizar os seguintes parâmetros:
“initial_date”: Data inicial para consultar movimentações da conta (Exemplo: "2022-01-03T18:59:00+00:00")
“final_date”: Data final para consultar movimentações da conta (Exemplo: "2022-01-03T19:00:00+00:00")
Observação: Deve ser respeitado o formato da data de acordo com os exemplos. 
 
Observação: Acessando a base pelo MongoDB, é possível verificar a data das movimentações
