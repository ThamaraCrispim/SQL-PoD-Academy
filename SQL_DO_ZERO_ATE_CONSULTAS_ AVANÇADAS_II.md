# 📘 Resumo – SQL | Aula 2 (Academia PoD)

A **Aula 2** aprofunda o uso da linguagem SQL, abordando criação de tabelas, chaves, joins, unions, case when, subconsultas, CTEs e funções avançadas. Esta aula complementa a Aula 1 e leva o aluno a um nível mais profissional na escrita de consultas.

---

## 1. Criação de Banco e Conexão

CREATE DATABASE nome_do_banco;
USE nome_do_banco;

---

## 2. Criação de Tabelas (DDL)

CREATE TABLE tbl_clientes (
    id INT NOT NULL AUTO_INCREMENT,
    nome VARCHAR(50),
    idade INT(3) UNSIGNED,
    PRIMARY KEY (id)
);

Regras comuns:
- NOT NULL
- AUTO_INCREMENT
- UNSIGNED
- PRIMARY KEY

---

## 3. CRUD – Operações Básicas

INSERT INTO tbl_cadastro_veiculo (placa, marca, ano)
VALUES ('ABC1234', 'Fiat', 2010);

SELECT * FROM tbl_cadastro_veiculo;

UPDATE tbl_cadastro_veiculo
SET cor = 'Preto'
WHERE placa = 'ABC1234';

DELETE FROM tbl_cadastro_veiculo
WHERE placa = 'ABC1234';

TRUNCATE TABLE tbl_cadastro_veiculo;

---

## 4. Chaves (PK e FK)

PRIMARY KEY (id)

FOREIGN KEY (id_marca) REFERENCES tbl_marca(id_marca)

ALTER TABLE tabela ADD PRIMARY KEY (id);
ALTER TABLE tabela ADD FOREIGN KEY (id_marca) REFERENCES tbl_marca(id_marca);

---

## 5. JOINS – Combinação de Tabelas

INNER JOIN:
SELECT a.placa, b.email
FROM cadastro_veiculo a
INNER JOIN cadastro_cliente b
ON a.placa = b.placa;

LEFT JOIN:
SELECT *
FROM A
LEFT JOIN B ON A.id = B.id;

RIGHT JOIN:
SELECT *
FROM A
RIGHT JOIN B ON A.id = B.id;

FULL JOIN:
SELECT *
FROM A
FULL JOIN B ON A.id = B.id;

---

## 6. UNION x UNION ALL

UNION ALL (mantém duplicados):
SELECT nome FROM t1
UNION ALL
SELECT nome FROM t2;

UNION (remove duplicados):
SELECT nome FROM t1
UNION
SELECT nome FROM t2;

---

## 7. CASE WHEN

SELECT 
    nome,
    CASE
        WHEN salario < 2000 THEN 'Baixo'
        WHEN salario BETWEEN 2000 AND 5000 THEN 'Médio'
        ELSE 'Alto'
    END AS faixa_salarial
FROM funcionarios;

---

## 8. Subconsultas (Subqueries)

WHERE:
SELECT nome
FROM cliente
WHERE id_cliente IN (
    SELECT id_cliente
    FROM vendas
    WHERE quantidade > 50
);

SELECT:
SELECT 
    id_produto,
    (SELECT AVG(valor) FROM produtos) AS media_produtos
FROM produtos;

---

## 9. CTE – Common Table Expressions

WITH total_vendas AS (
    SELECT id_funcionario, SUM(valor_venda) AS soma
    FROM tbl_vendas
    GROUP BY id_funcionario
)
SELECT *
FROM total_vendas
WHERE soma > 10000;

---

## 10. Funções Gerais

Strings:
CONCAT(col1, col2);
SUBSTR(nome, 1, 3);
REPLACE(coluna, 'a', 'b');
UPPER(coluna);
LOWER(coluna);
TRIM(coluna);
LENGTH(coluna);

Numéricas:
ROUND(200.55);
TRUNCATE(200.555, 2);
POWER(2, 3);
SQRT(25);
SUM(coluna);
AVG(coluna);
MIN(coluna);
MAX(coluna);
COUNT(*);

Datas:
DATEDIFF(data1, data2);
DAY(data);
MONTH(data);
YEAR(data);
HOUR(data);
MINUTE(data);
SECOND(data);

---

## 11. Window Functions

ROW_NUMBER:
SELECT 
    ROW_NUMBER() OVER (ORDER BY salario DESC) AS posicao,
    nome
FROM funcionarios;

RANK:
SELECT 
    RANK() OVER (ORDER BY valor DESC) AS ranking
FROM vendas;

LAG / LEAD:
SELECT 
    nome,
    total,
    LAG(total) OVER (PARTITION BY nome ORDER BY data) AS compra_anterior
FROM compras;

---

## 12. Ordem Correta da Execução SQL

1. FROM / JOIN
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY
7. LIMIT

