# 📘 Resumo – SQL | Aula 1 (Academia PoD)

A **Aula 1** apresenta os fundamentos essenciais da linguagem SQL, abrangendo desde o conceito de bancos relacionais até a construção de consultas completas com filtros, ordenações e agregações.

---

## 1. O que é SQL?
**SQL** (*Structured Query Language*) é a linguagem padrão para consultar, manipular e gerenciar dados em Bancos de Dados Relacionais.

* **História:** Criada na década de 70 (IBM) por Donald Chamberlin e Raymond Boyce. Inicialmente chamada de **SEQUEL**.
* **Aplicações:** Engenharia de Dados, Ciência de Dados, Desenvolvimento Web, BI e Áreas de Negócio.

---

## 2. Variações de SQL (Dialetos)
Embora exista um padrão (ANSI SQL), cada SGBD (Sistema Gerenciador de Banco de Dados) possui particularidades na sintaxe.

**Exemplo de variação para limitar linhas:**

| Função | MySQL | SQL Server | Oracle | SQLite/Postgres |
| :--- | :--- | :--- | :--- | :--- |
| **Limitar linhas** | `LIMIT 5` | `TOP 5` | `ROWNUM <= 5` | `LIMIT 5` |

---

## 3. Os 5 Tipos de Comandos SQL

### 🛠️ DDL – Data Definition (Estrutura)
Comandos para criar ou alterar a estrutura do banco.
* `CREATE` (Criar)
* `ALTER` (Alterar)
* `DROP` (Excluir estrutura)

### 📝 DML – Data Manipulation (Dados)
Comandos para mexer nos dados dentro das tabelas.
* `INSERT` (Inserir)
* `UPDATE` (Atualizar)
* `DELETE` (Deletar dados)

### 🔍 DQL – Data Query (Consulta)
O comando mais usado para análise.
* `SELECT` (Selecionar/Ler)

### 🔐 DCL – Data Control (Permissões)
* `GRANT` (Dar permissão)
* `REVOKE` (Retirar permissão)

### 💾 TCL – Transaction Control (Transação)
* `COMMIT` (Salvar definitivo)
* `ROLLBACK` (Desfazer)

---

## 4. DBeaver – Ferramenta da Aula

DBeaver é um software de administração de banco de dados usado para:
- Criar conexões
- Visualizar tabelas e colunas
- Executar consultas SQL

Na aula, utilizou-se o servidor:

Host: relational.fel.cvut.cz  
Port: 3306  
User: guest  
Pass: ctu-relational

---

## 5. Primeiras Consultas (SELECT)

Comandos básicos para ler dados.  
Nota: use sempre comandos em inglês (`SELECT`, `FROM`).

Selecionando colunas específicas:
```sql
SELECT placa, marca, ano
FROM tbl_cadastro_veiculo
LIMIT 5;
```

---

## 6. Tipos de Dados

Os principais tipos de dados encontrados nos bancos.

**Numéricos:**
- INT (inteiro)
- FLOAT / DECIMAL (com casas decimais)

**Texto:**
- VARCHAR (texto variável)
- CHAR (texto fixo)
- TEXT (textos longos)

**Datas:**
- DATE (data)
- DATETIME (data e hora)

---

## 7. Ordenação (ORDER BY)

Comando para organizar a visualização dos dados.

Ordenando do maior para o menor (Decrescente):
```sql
SELECT placa, marca, ano
FROM tbl_cadastro_veiculo
ORDER BY ano DESC
LIMIT 10;
```

---

## 8. Principais Operadores

Símbolos usados para fazer contas ou comparações.

**Aritméticos (Contas):**  
+ (Soma), - (Subtração), * (Multiplicação), / (Divisão)

**Comparação:**  
= (Igual), != (Diferente), > (Maior), < (Menor)

**Lógicos:**  
AND (E)  
OR (OU)  
NOT (NÃO)  
BETWEEN (Entre)  
LIKE (Parecido com...)  
IN (Está na lista...)

---

## 9. Filtros (WHERE)

Comando para filtrar linhas específicas na tabela.

**Filtro de texto exato:**
```sql
SELECT *
FROM tbl_cadastro_veiculo
WHERE marca = 'Fiat';
```

**Filtro com múltiplas condições (AND):**
```sql
SELECT *
FROM tbl_cadastro_veiculo
WHERE marca = 'Fiat' 
  AND ano = 2023;
```

**Filtro de faixa de valores (BETWEEN):**
```sql
SELECT *
FROM tbl_cadastro_veiculo
WHERE valor BETWEEN 2000000 AND 3000000;
```

---

## 10. Funções de Agregação

Funções matemáticas para resumir dados.

Calculando totais, médias e máximos:
```sql
SELECT 
    COUNT(placa) as total_carros,
    MAX(valor_tabela_fipe) as maior_valor,
    AVG(valor_tabela_fipe) as media_valor
FROM tbl_cadastro_veiculo;
```

---

## 11. Agrupamento (GROUP BY)

Agrupa os dados repetidos para aplicar funções de agregação.

**Média de valor por marca:**
```sql
SELECT 
    marca,
    AVG(valor_tabela_fipe) as media_valor
FROM tbl_cadastro_veiculo
GROUP BY marca;
```

**Máximo, Média e Mínimo por marca:**
```sql
SELECT 
    marca,
    MAX(valor_tabela_fipe),
    AVG(valor_tabela_fipe),
    MIN(valor_tabela_fipe)
FROM tbl_cadastro_veiculo
GROUP BY marca;
```

---

## 12. Filtro Pós-Agregação (HAVING)

Filtra os resultados depois que o agrupamento foi feito.

**Marcas com valor máximo acima de 10 milhões:**
```sql
SELECT 
    marca,
    MAX(valor_tabela_fipe)
FROM tbl_cadastro_veiculo
GROUP BY marca
HAVING MAX(valor_tabela_fipe) > 10000000;
```

---

## 13. Consulta Completa

Todos os comandos juntos na ordem correta.

Relatório final completo:
```sql
SELECT
    marca,
    MAX(valor_tabela_fipe) AS valor_max_fipe,
    AVG(valor_tabela_fipe) AS valor_media_fipe,
    MIN(valor_tabela_fipe) AS valor_min_fipe
FROM tbl_cadastro_veiculo
WHERE marca NOT IN ('Fiat', 'Audi', 'Ferrari')
  AND ano BETWEEN 1990 AND 2022
GROUP BY marca
HAVING MAX(valor_tabela_fipe) > 10000000
ORDER BY valor_max_fipe DESC
LIMIT 10;
```
