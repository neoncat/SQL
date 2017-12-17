MySQL 

********************************************************************************************************************

COMANDOS

Como criar uma base de dados: 

CREATE DATABASE nome_do_banco
DEFAULT CHARACTER SET utf8
DEFAULT COLLATE utf8_general_ci;

********************************************************************************************************************

Como selecionar a base de dados que será utilizada:

USE nome_do_banco;

********************************************************************************************************************

Como excluir uma base de dados:

DROP DATABASE nome_do_banco;

********************************************************************************************************************

Como setar a conexão para UTF8:

SET NAMES utf8;

********************************************************************************************************************

Como criar uma tabela com padrão InnoDB: 

CREATE TABLE nome_da_tabela(
id INT AUTO_INCREMENT PRIMARY KEY,
nome VARCHAR(35) NOT NULL,
email VARCHAR(35) NOT NULL,
senha VARCHAR(32) NOT NULL
)ENGINE = InnoDB
DEFAULT CHARSET = utf8;

********************************************************************************************************************

Como excluir uma tabela:

DROP TABLE nome_da_Tabela;

********************************************************************************************************************

Desativar a checagem de chave estrangeira ao excluir uma tabela:

SET foreign_key_checks = 0;

Ativar a checagem de chave estrangeira:

SET foreign_key_checks = 1;

********************************************************************************************************************

Como relacionar tabelas utilizando constraints:

CREATE TABLE tabela1(
id INT AUTO_INCREMENT,
descricao TEXT,
CONSTRAINT tabela1_id_pk PRIMARY KEY(id)
)ENGINE = InnoDB
DEFAULT CHARSET = utf8;

CREATE TABLE tabela2(
id INT AUTO_INCREMENT,
tb1_fk int,
at1 varchar(35),
at2 int,
at3 date,
at4 decimal(5,2),
CONSTRAINT tabela2_id_pk PRIMARY KEY(id),
CONSTRAINT tabela2_tb1_fk FOREIGN KEY(tb1_fk) REFERENCES tabela1(id)
)ENGINE = InnoDB
DEFAULT CHARSET = utf8;

********************************************************************************************************************

Como inserir um registro na tabela:

INSERT INTO tabela1 (descricao) VALUES ('texto...');

INSERT INTO tabela2 (at1, at2, at3, at4) VALUES ('texto de 35 caracteres...', 20, '2017-12-11', 327.75);

OBSERVAÇÕES

*Atributos do tipo caracteres devem estar entre aspas simples*

*Atributos numericos nao precisam de aspas*

*Atributos do tipo date começam com YYYY-MM-DD e devem estar entre aspas simples*

*Atributos do tipo decimal são para números reais e determinam a quantidade de digitos e casas decimais que o campo irá aceitar*

*Para numeros reais as casas decimais são separadas por ponto*

********************************************************************************************************************

Funçoes Nativas:

INSERT INTO tabela (senha) VALUES (md5('senha'));

*A função md5 transforma a string passada como parametro num codigo hash de 32 caracteres*

INSERT INTO tabela (data) VALUES (NOW()); 

*A função NOW() retorna a data e a hora do sistema operacional, usada em atributos do tipo date ou datetime*

********************************************************************************************************************

Como consultar os valores das colunas

SELECT * FROM tabela;

SELECT nome_da_coluna FROM tabela;

********************************************************************************************************************

Como consultar tabelas relacionadas;

SELECT tabela1.nome_da_coluna, tabela2.nome_da_coluna FROM tabela2 INNER JOIN tabela1 ON tabela1.nome_da_coluna = tabela2.nome_da_coluna;

********************************************************************************************************************

Como colocar apelidos para as colunas:

SELECT nome_da_coluna AS apelido FROM tabela;

********************************************************************************************************************

Como colocar apelidos em tabelas:

SELECT apelido.nome_da_coluna FROM tabela AS apelido;

********************************************************************************************************************

Como criar uma view:

CREATE VIEW nome_da_view AS (informe a query que será chamada)



