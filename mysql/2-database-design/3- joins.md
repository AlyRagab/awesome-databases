#### Explanation about Joins :
- Joins Diagram :

<img src="https://github.com/AlyRagab/databases-for-devops/blob/master/mysql/images/joins.png" />

- Simply JOINs is a way in SQL to access data from multiple tables.
- Types of JOINs `Inner Join` , `RIGHT JOIN` , `LEFT JOIN` , `FULL JOIN`.
  - Inner Join:
    - It makes the Query to take every selected data from table-A and combine it with every 
       selected data from table-B.
    - Example : 
    ```
    select concat(first_name, ' ', last_name) AS 'Client_Name', products.product_name AS 'Product Name', orders.order_number AS 'Order Number', orders.order_date AS 'Order Date'
    from orders
    inner join products on orders.id = products.id
    inner join clients on orders.id = clients.id;
    ```
    - Very useful when we need to have all matched data between two tables.
  
  - Left Join:
    - It will list ALL data in the left table first , then match it with the right table.
    - This may lead to have a "NULL" values in the right table , as may be a data in the left table not match the selection
      criteria.
    - Example :
    ```
    select concat(first_name , ' ', last_name) AS "Client_Name", products.product_name AS "Product Name", orders.order_number AS "Order Number", orders.order_date AS "Order Date"
    from orders
    left join products on orders.id = products.id
    left join clients on orders.id = clients.id;
    ```
    - Very useful once we need to get a clients who have no orders.

  - Right Join:
    - The exact opposite of the left join.
    - Used to get an information about the products we have but not purchased yet or may be
      the names of the clients did not entered to the system , "Null" values in the left table.
    - Example :
    ```
    select concat(first_name , ' ', last_name) AS "Client_Name", products.product_name AS "Product Name", orders.order_number AS "Order Number", orders.order_date AS "Order Date"
    from orders
    right join products on orders.id = products.id
    right join clients on orders.id = clients.id;
    ```

  - Full Join:
    - To get all data from both tables , and we may have a "Null" values.
    - A combination of both Right & Left join together , So "Null" is expected in both columns.
    - Example :
    ```
    select concat(clients.first_name, ' ', clients.last_name) AS "Client Full Name", products.product_name AS "Product Name"
    from clients
    left join products on clients.client_id = products.product_id

    union 

    select concat(clients.first_name, ' ', clients.last_name) AS "Client Full Name", products.product_name AS "Product Name"
    from clients
    right join products on clients.client_id = products.product_id;
    ```
    - We get the full data in both tables and then we use `UNION` to get it together in one table
      If we use `UNION ALL` we will get duplicate data as well.


