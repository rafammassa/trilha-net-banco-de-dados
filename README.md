  ### Comandos SQL

SELECT * FROM Clientes
▶ seleciona todas as colunas da tabela

SELECT Nome, Sobrenome, Email FROM Clientes
▶ seleciona somente as colunas escritas as colunas da tabela

WHERE Nome = 'Adam'
▶ mostra apenas as linhas da tabela onde o nome é Adam

WHERE Nome = 'Adam' AND Sobrenome = 'Reynolds'
▶ mostra as linhas da tabela onde o nome é Adam E o sobrenome é Reynolds

WHERE Nome = 'Adam' OR Sobrenome = 'Reynolds'
▶ mostra as linhas da tabela onde o nome é Adam OU o sobrenome é Reynolds

WHERE Nome LIKE 'G%'
▶ mostra as linhas onde os nomes COMEÇAM com G

WHERE Nome LIKE '%G%'
▶ mostra as linhas onde os nomes TÊM G

ORDER BY Nome, Sobrenome
▶ ordenando por nome e depois sobrenome em ordem crescente

ORDER BY Nome, Sobrenome DESC
▶ ordenando por nome e depois sobrenome em ordem decrescente

INSERT INTO Clientes (Nome, Sobrenome, Email, AceitaComunicados, DataCadastro)
VALUES ('Rafaella', 'Massa', 'email@email.com', 1, GETDATE())
OU
INSERT INTO Clientes VALUES ('Eduardo', 'Folco', 'email@email.com', 0, GETDATE())
▶ inserindo nova linha na tabela

UPDATE Clientes
SET Email = 'emailatualizado@email.com',
	  AceitaComunicados = 0
WHERE Id = 1002
▶ fazendo update de email e aceitacomunicados (sempre pelo ID)

DELETE Clientes
WHERE Id = 1001
▶ deletando linha

BEGIN TRAN
ROLLBACK
▶ fazer antes de mexer com delete

CREATE TABLE Produtos (
	Id int IDENTITY(1, 1) PRIMARY KEY NOT NULL,
	Nome varchar(255) NOT NULL,
	Cor varchar(50),
	Preco decimal(13, 2) NOT NULL,
	Tamanho varchar(5),
	Genero char(1)
)
▶ criando tabela

SELECT COUNT(*) FROM Produtos
▶ contagem de linhas sem retorno de dados

SELECT COUNT(*) QuantidadeProdutos FROM Produtos
▶ contagem de linhas sem retorno de dados dando um nome a coluna

SELECT COUNT(*) QuantidadeProdutosM FROM Produtos WHERE Tamanho = 'M'
▶ contagem de linhas onde o Tamanho é M sem retorno de dados dando um nome a coluna

SELECT SUM(Preco) ValorTotal FROM Produtos
▶ somando valor total de todas as linhas (também funciona com WHERE)

SELECT MAX(Preco) ValorMaximo FROM Produtos
▶ valor máximo da coluna

SELECT MIN(Preco) ValorMinimo FROM Produtos
▶ valor mínimo da coluna

SELECT AVG(Preco) Media FROM Produtos
▶ média das linhas

SELECT 
	Nome + ' - ' + Cor NomeProdutoCompleto
FROM Produtos
▶ concatenando colunas

SELECT 
	Nome + ' - ' + Cor NomeProduto,
	UPPER(Nome) NomeMaiusculo,
	LOWER(Cor) CorMinuscula
FROM Produtos
▶ deixando a coluna toda maiúscula ou toda minúsucla

ALTER TABLE Produtos
ADD DataCadastro DATETIME2

UPDATE Produtos SET DataCadastro = GETDATE()
▶ criando uma coluna e já fazendo update dela

ALTER TABLE Produtos
DROP COLUMN DataCadastro
▶ apagando coluna 

FORMAT(DataCadastro, 'dd/MM/yyyy HH:mm') DataFormatada
▶formatando data

SELECT 
	Tamanho,
	COUNT(*) Quantidade
FROM Produtos
WHERE Tamanho <> ''
GROUP BY Tamanho 
ORDER BY Quantidade
▶ agrupando com group by

SELECT * FROM Clientes
SELECT * FROM Enderecos

INSERT INTO Enderecos VALUES (4, 'Rua teste', 'Bairro teste', 'Cidade teste', 'SP')

CREATE TABLE Enderecos (
		Id int PRIMARY KEY IDENTITY (1, 1) NOT NULL,
		IdCliente int,
		Rua varchar (255),
		Bairro varchar (255),
		Cidade varchar (255),
		Estado char(2)

		CONSTRAINT FK_Enderecos_Clientes FOREIGN KEY (IdCliente)
		REFERENCES Clientes(Id)
)
▶ referenciando com foreign key

SELECT
	*
FROM
	Clientes
INNER JOIN Enderecos ON Clientes.Id - Enderecos.IdCliente
WHERE Cliente.Id = 4
▶ j8ntando com join

*CTRL + K + C = comentário
