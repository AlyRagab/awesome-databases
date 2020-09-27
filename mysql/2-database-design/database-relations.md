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
   client_date datetime default current_timestamp,
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

