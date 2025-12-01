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
## 4. Realize uma consulta na tabela `employees` selecionando as colunas `first_name`, `last_name`, `birth_date`, ordenando pelo `birth_date` de maneira decrescente e limitando o retorno em 10 registros.  
Baseando-se na data de nascimento, qual o nome do(s) funcionário(s) mais novo(s)?

### **Comando SQL utilizado:**
```sql
SELECT first_name, last_name, birth_date
FROM employees
ORDER BY birth_date DESC
LIMIT 10;
```
***Print do resultado no mysql**


![exercicio3](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/lista1-exercicio4.png)
## 5.Consultando a tabela `employees`, qual a data mais antiga de contratação (`hire_date`)?

### **Comando SQL utilizado:**
```sql
SELECT first_name, last_name, hire_date
FROM employees
ORDER BY hire_date ASC
LIMIT 1;
```
***Print do resultado no mysql***


![exercicio05](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/Lista1-exercicio5.png)

## 6 Consultando a tabela `employees`, qual a quantidade de funcionários do sexo feminino que foram contratados depois da data `1990-12-02`?

### **Comando SQL utilizado:**
```sql
SELECT COUNT(*) AS total_feminino_contratado
FROM employees
WHERE gender = 'F'
  AND hire_date > '1990-12-02';
  ```
***Print do resultado no mysql***


![exercicio06](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/lista1-exercicio6.png)

## 7. Consultando a tabela `employees`, existem mais funcionários do sexo feminino ou masculino?

### **Comando SQL utilizado:**
```sql
SELECT gender, COUNT(*) AS total
FROM employees
GROUP BY gender;
 ```
***Print do resultado no mysql***


![exercicio07](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/lista1-exercicio7.png)


## 8. Consultando a tabela `titles`, qual a quantidade de registros?

### **Comando SQL utilizado:**
```sql
SELECT COUNT(*) AS total
FROM titles;
```

***Print do resultado no mysql***


![exercicio08](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/lISTA1-exercicio8.png)
