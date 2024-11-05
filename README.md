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

*CTRL + K + C = comentário
