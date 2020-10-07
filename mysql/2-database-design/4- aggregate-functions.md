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
   - This will prnit how many products per client
```
select first_name, product_name, count(*) as "Product Count"
from orders
join products on orders.product_id = products.id
join clients on orders.client_id = clients.id
group by first_name, product_name
order by first_name;
```
  - Getting how many times the product is sold 
```
select product_name AS "Product Name", count(*) AS "Product Count"
from orders
join products on orders.product_id = products.id
group by products.product_name;
```

