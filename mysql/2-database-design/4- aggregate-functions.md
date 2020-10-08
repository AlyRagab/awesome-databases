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
 - `SUM` function :
   - Getting the Sum "Total sold payment per product" :
```
select client_name, product_name, product_price AS "Original Price", count(*) AS "Product Count", sum(product_price) AS "Total in US"
from orders
join products on orders.product_id = products.id
join clients on orders.client_id = clients.id
group by client_name, product_price, product_name
order by client_name;
```
  - `AVG` function :
    - Getting the AVG number of the sold products :
```
select client_name, product_name, avg(product_price) AS "Average in US"
from orders
join products on orders.product_id = products.id
join clients on orders.client_id = clients.id
group by client_name, product_price, product_name
order by client_name;
```
  - `MIN` and `MAX` functions :
    - Getting Minimum values / Maximum Values :
```
1- Minimum Product Price :
select product_name, product_price
from products
where product_price = ( select min(product_price) from products);

2- Maximum Product Price :
select product_name, product_price
from products
where product_price = ( select max(product_price) from products);
```
