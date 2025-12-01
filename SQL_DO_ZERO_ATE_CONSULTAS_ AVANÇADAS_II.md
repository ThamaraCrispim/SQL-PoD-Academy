# 📘 Resumo – SQL | Aula 2 (Academia PoD)

A Aula 2 aprofunda conceitos fundamentais de SQL, introduzindo criação de estruturas, manipulação de dados, relacionamentos entre tabelas e operações avançadas como joins, unions, subconsultas, CTEs e funções de janelamento.

---

## 1. Criação de Banco e Conexão

```sql
CREATE DATABASE nome_do_banco;
USE nome_do_banco;
```

---

## 1.1 Criação de Tabelas

```sql
CREATE TABLE tbl_clientes (
    id INT NOT NULL AUTO_INCREMENT,
    nome VARCHAR(50),
    idade INT(3) UNSIGNED
);
```

---

## 2. CRUD – Create, Read, Update, Delete

O CRUD representa as quatro operações básicas em Bancos de Dados Relacionais.

### ➤ Create (Inserir)

```sql
INSERT INTO tbl_cadastro_veiculo 
(placa, marca, modelo, flag_veiculo_novo, ano, cor, uf, valor_tabela_fipe, data_cadastro)
VALUES 
('AG2D3D5', 'Fiat', 'Uno', 0, 2005, 'Azul', 'SP', 22000.0, '2005-09-02 14:40:54');
```

### ➤ Read (Consultar)

```sql
SELECT *
FROM tbl_cadastro_veiculo;
```

### ➤ Update (Atualizar)

```sql
UPDATE tbl_cadastro_veiculos
SET uf = 'São Paulo'
WHERE uf = 'SP';
```

### ➤ Delete (Excluir)

```sql
DELETE FROM tbl_cadastro_veiculos
WHERE uf = 'SP';
```

---

## 3. Chaves Primárias (PK) e Estrangeiras (FK)

### ➤ Primary Key

```sql
CREATE TABLE tbl_cadastro_veiculo (
    placa CHAR(7) NOT NULL,
    marca VARCHAR(50),
    modelo VARCHAR(50),
    PRIMARY KEY (placa)
);
```

### ➤ Foreign Key

```sql
ALTER TABLE tbl_cadastro_veiculo
ADD FOREIGN KEY (id_marca) REFERENCES tbl_marca_veiculo(id_marca);
```

---

## 4. Joins – Combinando Tabelas

### ➤ INNER JOIN

```sql
SELECT a.placa, a.marca, b.cpf
FROM cadastro_veiculo a
INNER JOIN cadastro_cliente b
ON a.placa = b.placa;
```

### ➤ LEFT JOIN

```sql
SELECT a.placa, a.marca, b.cpf
FROM cadastro_veiculo a
LEFT JOIN cadastro_cliente b
ON a.placa = b.placa;
```

### ➤ RIGHT JOIN

```sql
SELECT a.placa, a.marca, b.cpf
FROM cadastro_veiculo a
RIGHT JOIN cadastro_cliente b
ON a.placa = b.placa;
```

### ➤ FULL JOIN

```sql
SELECT a.placa, a.marca, b.cpf
FROM cadastro_veiculo a
FULL JOIN cadastro_cliente b
ON a.placa = b.placa;
```

---

## 5. UNION x UNION ALL

### ➤ UNION ALL (Mantém duplicatas)

```sql
SELECT nome, idade FROM tbl_cadastro_1
UNION ALL
SELECT nome, idade FROM tbl_cadastro_2;
```

### ➤ UNION (Remove duplicatas)

```sql
SELECT nome, idade FROM tbl_cadastro_1
UNION
SELECT nome, idade FROM tbl_cadastro_2;
```

---

## 6. CASE WHEN – Criando Categorias

```sql
SELECT
    nome,
    CASE
        WHEN salario <= 2000 THEN 'até 2000'
        WHEN salario BETWEEN 2000 AND 4000 THEN '2k a 4k'
        WHEN salario > 8000 THEN 'acima de 8000'
        ELSE 'não informado'
    END AS faixa_salarial
FROM tbl_funcionario;
```

---

## 7. Subconsultas (Subqueries)

### ➤ Subquery no WHERE

```sql
SELECT nome
FROM tbl_cliente
WHERE id_cliente IN (
    SELECT id_cliente
    FROM tbl_vendas
    WHERE quantidade > 50
);
```

### ➤ Subquery como coluna

```sql
SELECT 
    id_produto,
    (SELECT AVG(valor) FROM tbl_produtos) AS media_valor
FROM tbl_produtos;
```

---

## 8. CTE – Common Table Expressions

```sql
WITH total_vendas AS (
    SELECT 
        id_funcionario,
        SUM(valor_venda) AS soma_vendas
    FROM tbl_vendas
    GROUP BY id_funcionario
)
SELECT *
FROM total_vendas
WHERE soma_vendas > 10000;
```

---

## 9. Funções Gerais

### ➤ Strings

```sql
SELECT CONCAT(nome, ' ', sobrenome) FROM funcionarios;
SELECT SUBSTR(nome,1,1) FROM funcionarios;
SELECT REPLACE(nome,'Ana','Maria') FROM funcionarios;
SELECT UPPER(nome) FROM funcionarios;
SELECT TRIM('  teste  ');
SELECT LENGTH(nome) FROM funcionarios;
```

### ➤ Numéricas

```sql
SELECT GREATEST(1,5,2);
SELECT POWER(2,3);
SELECT ROUND(200.445,2);
SELECT TRUNCATE(200.556,2);
SELECT SQRT(25);
```

### ➤ Datas

```sql
SELECT DATEDIFF('2022-01-31','2022-01-01');
SELECT YEAR('2022-01-01');
SELECT MONTH('2022-01-01');
SELECT DAY('2022-01-01');
```

---

## 10. Funções de Janelamento (Window Functions)

### ➤ ROW_NUMBER

```sql
SELECT
    ROW_NUMBER() OVER (ORDER BY emp_no) AS ranking,
    emp_no
FROM employees;
```

### ➤ RANK / DENSE_RANK

```sql
SELECT
    DENSE_RANK() OVER (ORDER BY valor DESC) AS ranking,
    valor
FROM tabela;
```

### ➤ LAG / LEAD

```sql
SELECT
    nome,
    data_compra,
    total,
    LAG(total) OVER (PARTITION BY nome ORDER BY data_compra) AS compra_anterior
FROM compras;
```

---

## 11. Ordem de Execução do SQL

1. FROM / JOIN  
2. WHERE  
3. GROUP BY  
4. HAVING  
5. SELECT  
6. ORDER BY  
7. LIMIT  
