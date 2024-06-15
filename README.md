-- Criação do banco de dados e seleção do mesmo
CREATE DATABASE escolaDB;
USE escolaDB;

-- 1. Criação da tabela 'estudantes' e inserção de dados
CREATE TABLE estudantes (
    nome VARCHAR(30) NOT NULL, 
    data_nascimento DATE,
    curso VARCHAR(30),
    matricula INT NOT NULL, 
    PRIMARY KEY(matricula)
);

INSERT INTO estudantes (nome, data_nascimento, curso, matricula) VALUES 
    ('Ryan', '2006-06-07', 'DS', 123),
    ('Renan', '2005-07-01', 'DS', 234),
    ('Aléxia', '2005-10-02', 'Multimídia', 345);

SELECT nome, matricula, data_nascimento FROM estudantes;

-- 2. Exclusão de um estudante específico
DELETE FROM estudantes WHERE matricula = 345;

-- 3. Atualização de dados de um estudante específico
UPDATE estudantes SET data_nascimento = '2004-12-05' WHERE matricula = 234;

-- 4. Tornar permanentes as alterações realizadas
COMMIT;

-- 5. Desfazer alterações feitas em uma transação (se o commit não tiver sido utilizado)
ROLLBACK;

-- 6. Seleção de todos os estudantes com suas informações
SELECT nome, matricula, data_nascimento, curso FROM estudantes;

-- 7. Seleção de estudantes nascidos após 1º de janeiro de 2005
SELECT * FROM estudantes WHERE data_nascimento > '2005-01-01';

-- 8. Seleção dos nomes e cursos dos estudantes
SELECT nome, curso FROM estudantes;

-- 9. Seleção dos nomes dos estudantes em ordem alfabética
SELECT nome FROM estudantes ORDER BY nome ASC;

-- 10. Contagem de estudantes por curso
SELECT curso, COUNT(*) AS total_estudantes FROM estudantes GROUP BY curso;
