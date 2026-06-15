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


**Read:** O Read como o próprio nome diz, é a operação que rege tudo que é relacionado a leitura de dados, então sempre que precisarmos trazer dados podemos utilizar uma imensidão de comandos `SELECT` para trazer esses dados, ai vamos ter por exemplo o mais simples de todos que seria `SELECT * FROM cliente` onde * representa as colunas selecionadas do nosso banco, nesse caso * traria todas as colunas, seguindo com o exemplo de cima traria Id, nome e idade já cliente seria o nossa tabela, nisso existem muitas variantes que não cabem aqui na explicação dos conceitos como Left join, right join e muito mais coisa.


**Update:** O Update é uma quatro operações, sendo ela a responsável por atualizar os dados nas tabelas, junto do Delete ele é um dos comandos que mais precisamos tomar cuidado pois uma query mal escrita pode impactar milhões de linhas de clientes reais e causar uma perca absurda caso você não tenha backup. É claro que um júnior dificilmente tem acesso pra rodar comandos desse tipo mas vai saber né. Uma das formas de realizar o update seria através do seguinte comando

```SQL
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```
Um detalhe importante é, não importa que tenhamos uma quebra de linha ou não, o que define o fim do comando é o ; o que pode ocasionar em diversos problemas caso você esteja criando uma procedure grande e coloque um ; no lugar errado fazendo com que o comando rode de forma diferente impactando diretamente os dados.

**Delete:** Por fim, temos o comando que poucas pessoas tem acesso em ambientes sérios de produção, o Delete, ele é responsável por deletar os dados da nossa aplicação, como uma medida protetiva, para essa função realizar efeito, temos dois comandos extras para auxiliar nesse manuseio, o primeiro deles é o COMMIT, ele é responsável por dizer que os dados de fato serão apagados, apenas utilizar o DELETE não garante que eles irão sumir, para isso temos um comando que nos auxilia a trazer esses dados de volta caso não tenhamos realizado o COMMIT ainda, que é o ROLLBACK.