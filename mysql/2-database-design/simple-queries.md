#### Before we dive into Database Design , Let's do some simple queries :

- First , Create the Database called 'store' and table called clients then add some data into it:
```
CREATE DATABASE store;
use store;
create table clients(
	id INT NOT NULL auto_increment,
    first_name VARCHAR(200),
    last_name VARCHAR(200),
    email VARCHAR(100),
    PRIMARY KEY(id)
);

insert into customers(first_name, last_name, email ) values('aly', 'ragab', 'alyragab70@gmail.com');
insert into customers(first_name, last_name, email) values('mohamed', 'aly', 'mohamed@gmail.com');
insert into customers(first_name, last_name, email) values('omar', 'aly', 'omar@gmail.com');
insert into customers(first_name, last_name, email) values('mahmoud', 'ragab', 'mahmoud@gmail.com');
insert into customers(first_name, last_name, email) values('mohamed', 'ragab', 'mragab@gmail.com');
insert into customers(first_name, last_name, email) values('ahmed', 'hassan', 'ahmed@gmail.com');
```
- Let's run simple queries :
```
select * from clients;
select first_name, last_name from clients;
select first_name, last_name from clients where id=3;
select first_name, last_name from clients where id between 1 and 4;
select first_name, last_name from clients where id > 4;
```