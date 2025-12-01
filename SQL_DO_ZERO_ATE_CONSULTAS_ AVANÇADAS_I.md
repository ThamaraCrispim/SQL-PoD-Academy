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

## 4. Ferramenta: DBeaver
Software universal para administração de bancos de dados.
* **Conexão utilizada na aula:**

```text
Server: relational.fel.cvut.cz  
Port:   3306  
User:   guest  
Pass:   ctu-relational

## 5. Primeiras Consultas (SELECT)

Comandos básicos para ler dados.
*Nota: Use sempre comandos em Inglês (`SELECT`, `FROM`).*

**Selecionando colunas específicas:**
```sql
SELECT placa, marca, ano
FROM tbl_cadastro_veiculo
LIMIT 5;
