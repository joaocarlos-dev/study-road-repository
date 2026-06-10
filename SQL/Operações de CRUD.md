Bom, primeiro de tudo, o que é CRUD? CRUD nada mais é do que um acrônimo de 4 operações que regem as interações com o banco de dados, sendo elas: 

1. Create
2. Read
3. Update
4. Delete

**Create:** Como o próprio nome diz, create é a operação responsável por criar novos dados dentro das tabelas do nosso banco de dados, vamos imaginar o seguinte, você possui uma tabela chamada "cliente" e dentro dessa tabela você tem lá as colunas Id, nome e idade
![[{CB005328-A851-486F-8F6E-57FCF1655A62}.png]]

Digamos que o cliente foi lá e preencheu um formulário, assim que ele preencher esse formulário é disparado para sua API uma solicitação para registrar esse cara dentro do banco, a API vai, se conecta no banco através de uma junção de comandos que dependem do seu banco de dados escolhido, como por exemplo PostgreSQL ou MySQL, um exemplo de comando seria esse 

```SQL
INSERT INTO cliente VALUES (1, 'João', 23);
```
 de qualquer forma, qualquer que seja o banco de dados o resultado deve ser o mesmo, inserir esse registro dentro do banco para ser utilizado em futuras consultas, dessa forma.
![[{7E4C8D5F-9B01-4EFD-B555-B7D4E0AAD9AE}.png]]