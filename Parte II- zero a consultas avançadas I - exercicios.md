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

Liste todos os álbuns cadastrados no banco de dados junto com o nome do artista responsável.
Exiba na consulta os campos: ID do Álbum, Título do Álbum e Nome do Artista.

### **Comando SQL utilizado:**

```sql
SELECT 
    a.AlbumId,
    a.Title,
    b.Name AS ArtistName
FROM album a
INNER JOIN artist b 
    ON a.ArtistId = b.ArtistId;

```
***Print do resultado no mysql**
![exercicio3.1](https://github.com/ThamaraCrispim/SQL-PoD-Academy/blob/main/imagens/lista%202%20-%20quest%C3%A3o%204.png)
