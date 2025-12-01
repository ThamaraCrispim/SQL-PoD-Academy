### 1. Descreva o nome e tipo de cada coluna da tabela employees.

**Comando SQL utilizado:**
```sql
DESCRIBE employees;
```

**Resposta:**

- **emp_no:** INT (Número Inteiro – Identificador)  
- **birth_date:** DATE (Data)  
- **first_name:** VARCHAR (Texto Variável)  
- **last_name:** VARCHAR (Texto Variável)  
- **gender:** ENUM ou CHAR (Texto Fixo 'M'/'F')  
- **hire_date:** DATE (Data)

**Print do resultado no mysql:**

![Descrição da tabela employees](https://raw.githubusercontent.com/ThamaraCrispim/SQL-PoD-Academy/main/imagens/Lista1-exercicio1.png)

## 2. Quais são as tabelas disponíveis no database `employees`?

### **Comando SQL utilizado:**
```sql
SELECT * FROM Employyes;
```
**Print do resultado no mysql:*

![Descrição da tabela employeesI](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/Lista1-exercicios2.png)

## 3. Realize uma consulta na tabela `employees` selecionando todas as colunas e limitando o retorno em 20 registros.

### **Comando SQL utilizado:**
```sql
SELECT * FROM employees
LIMIT 20;
```
**Print do resultado no mysql:*

![exercicio3](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/lista1-exercicio3.png)
