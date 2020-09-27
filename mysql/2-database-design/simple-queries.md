#### MySQL Data Types :
- [Official Reference](https://dev.mysql.com/doc/refman/8.0/en/data-types.html)

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
- Let's run simple queries using DDL :
```
1- Using Select :
select * from clients;
select first_name, last_name from clients;
select first_name, last_name from clients where id=3;
select first_name, last_name from clients where id between 1 and 4;
select first_name, last_name from clients where id > 4;
select distinct first_name from clients; ## This will remove any duplication.
select concat(first_name ,' ', last_name) AS 'Name' from clients; ## Grouping two rows into one column

2- Using Alter :
alter table clients add city VARVHAR(50); ## Adding aditional column
alter table clients remove city; ## Removing a column
alter table clients modify city varchar(100) ## Modifying the data type of a column

3- Using Update :
update clients set city = 'London' where id=4;
4- Using Delete :
delete from clients where id =5;
```