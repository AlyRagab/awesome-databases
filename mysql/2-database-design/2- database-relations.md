#### Database Design in details :
- Database Diagram :
<img src="https://github.com/AlyRagab/databases-for-devops/blob/master/mysql/images/online-store.png" />

- So According to this diagram , Let's design our online store database as below :
```
create database store;
use store;

create table clients(
  id int not null auto_increment,
  first_name varchar(50),
  last_name varchar(50),
  email varchar(100),
  city varchar(50),
  primary key(id)
);

create table products(
  id int not null auto_increment,
  product_name varchar(200),
  product_price int,
  primary key(id)
);

create table orders(
   id int not null auto_increment,
   order_number int,
   product_id int,
   client_id int,
   order_date datetime default current_timestamp,
   primary key(id),
   foreign key(product_id) references products(id),
   foreign key(client_id) references clients(id)
);

```
- Inserting Data into Tables :
```
insert into clients(first_name, last_name, email, city) 
values ('Aly', 'Ragab', 'aly@example.com', 'london'),
       ('Mohamed', 'Aly', 'mohamed@example.com', 'berlin'),
       ('John', 'Smith', 'johm@abc.com', 'paris'),
       ('Sam' , 'Adam', 'sam@company.com', 'amesterdam');

insert into products(product_name, product_price)
values ('IMac' , 3000),
       ('MacBook Pro', 2500),
       ('Apple Watch', 1000),
       ('NoteBook' , 1500);
       
insert into orders(order_number, product_id, client_id)
values (001, 4, 1),
       (002, 2, 4),
       (003, 1, 3),
       (004, 3, 2);
```

- Running some select queries :
  - Getting the Client_Name , their Products_Name , Order_Number and Order_Date 
  Using Inner Join:
```
select concat(first_name, ' ', last_name) AS 'Client_Name', products.product_name AS 'Product Name', orders.order_number AS 'Order Number', orders.order_date AS 'Order Date'
from orders
inner join products on orders.id = products.id
inner join clients on orders.id = clients.id;
```
  - Using the Self Join :
```
select concat(first_name, ' ', last_name) AS 'Client_Name', products.product_name AS 'Product Name', orders.order_number AS 'Order Number', orders.order_date AS 'Order Date'
from orders , products , clients
where orders.id = products.id and orders.id = clients.id;
```

