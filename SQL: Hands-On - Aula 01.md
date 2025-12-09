# 📚 Aula 1 – Introdução ao SQL  
---

# 🧠 O que é SQL?

SQL (*Structured Query Language*) é a linguagem padrão utilizada para **gerenciar e manipular bancos de dados relacionais**. Criada pela IBM na década de 1970, ela permite realizar consultas, inserções, atualizações, exclusões e controle completo das estruturas de dados.

Com SQL você pode:
- Consultar dados de forma eficiente  
- Inserir e alterar informações  
- Excluir registros  
- Criar e modificar tabelas  
- Controlar permissões e transações  
- Garantir integridade e organização dos dados  

Os dados são armazenados em **tabelas**, com linhas (registros) e colunas (campos), permitindo o uso de **relacionamentos**.

---

# 🗄️ SGBD – Sistema Gerenciador de Banco de Dados

Um SGBD é o software que armazena e gerencia bancos de dados. Exemplos:

- MySQL  
- PostgreSQL  
- SQL Server  
- Oracle  
- SQLite  
- MariaDB  

Mesmo existindo padrões definidos pela ANSI/ISO, cada SGBD possui extensões próprias:

- SQL Server → **T-SQL**  
- Oracle → **PL/SQL**  
- PostgreSQL → Funções e operadores específicos  
- MySQL → Engines e tipos próprios  

---

# 🧩 Subconjuntos da Linguagem SQL

| Categoria | Nome | Função |
|----------|------|--------|
| **DDL** | Data Definition Language | Estrutura do banco |
| **DML** | Data Manipulation Language | Manipulação de dados |
| **DQL** | Data Query Language | Consultas |
| **DCL** | Data Control Language | Permissões |
| **TCL** | Transaction Control Language | Transações |

---

# 🔨 1. DDL — *Data Definition Language*  
Comandos para criar e modificar a estrutura do banco.

### Principais comandos:
- `USE`
- `CREATE`
- `ALTER`
- `DROP`
- `TRUNCATE`

---

## Exemplos de DDL

### Criar banco + Selecionar banco
```sql
CREATE DATABASE Loja;
USE Loja;

