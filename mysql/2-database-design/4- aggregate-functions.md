#### Useful SQL Aggregate Functions :
 - `COUNT` function:
   - It counts records based on pattern.
```
select count(*) from clients; ## counts all records
select count(first_name) from clients;
select count(distinct first_name, last_name) from clients; ## Will count the names without duplication.
select count(*) from clients where first_name like '%A'; ## counts whatever names starting with 'A'
```

 - `GROUP BY` function :
   - Aggregates a data into a single rows.
```
## This will prnit how many product per client :
select name AS "Client Name", product_name AS "Product Name", count(*) AS "Product Count" 
from clients, products
group by clients.name, products.product_name;
```
 
 - Aggregates a data from two tables :
 ```
select first_name, product_name, count(*)
from clients
join orders on clients.id = orders.client_id
group by first_name, product_name;
 ``` 