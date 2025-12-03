## Questão 3  
Para os clientes que não têm empresa cadastrada, altere a tabela e preencha a coluna **Company** com empresas fictícias (não precisa ser uma empresa diferente por cliente).

### **Comando SQL utilizado:**

```sql
SELECT 
    FirstName,
    CustomerId,
    LastName,
    Company,
    Address
FROM 
    customer;
```

***Print do resultado no mysql**

![exercicio3](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/Lista%202%20-%20quest%C3%A3o%203.png)

``` sqp
UPDATE customer
SET Company = 'Nacional Pet'
WHERE Company IS NULL
  AND CustomerId > 0;
```
***Print do resultado no mysql**


![exercicio3.1](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/lista%202%20-%20quest%C3%A3o%203.1.png)


## Questão 4. 

Um cliente reclamou de uma nota fiscal gerada, ele informou que o número da nota era 10 e ele pede pra confirmar todas as músicas que
ele comprou, pode gerar uma consulta com os campos : Nome do Cliente, Número da Nota , Música , Preço Unitário ? 
