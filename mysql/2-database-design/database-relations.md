#### Database Design in details :
- Database Diagram :
-  <img src="https://github.com/AlyRagab/databases-for-devops/blob/master/mysql/images/online-store.png" />
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
   client_date datetime default current_timestamp,
   primary key(id),
   foreign key(product_id) references products(id),
   foreign key(client_id) references clients(id)
);

```
