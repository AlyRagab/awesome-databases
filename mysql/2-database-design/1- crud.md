#### MySQL Data Types :
- [Official Reference](https://dev.mysql.com/doc/refman/8.0/en/data-types.html)
- `CHAR` vs `VARCHAR` ?
  - Both are Used for storing text or string , but `Char` has a fixed length while 
  `VARCHAR` is vary.
  - `CHAR(20)` means only 20 characters allowed.
  - `CHAR` used when we need to store something like "country code , flags like Y/N ...etc"
  otherwise we use `VARCHAR`.
- `DECIMAL` :
  - we use it for storing numbers like "19.2" as `DECIMAL(3.1)` or 111.33 `DECIMAL(5.2)`
  so if `DECIMAL(5.2)` means that the total digits are `5` and decimal is `2`.
- `DATE` and `DATETIME` :
  - `DATE` for storing dates without time like this format `YYYY-MM-DD`.
  - `DATETIME` for storing date with times like this format `YYYY-MM-DD HH:MM:SS`,
   we use `default CURRENT_TIMESTAMP` for more flixbility.
  - `TIME` for storing time without date like this format `HH:MM:SS`.

#### Before we dive into Database Design , Let's do some simple queries :
- CRUD Operations "Create , Read , Update and Delete"
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

insert into customers(first_name, last_name, email ) 
values('aly', 'ragab', 'alyragab70@gmail.com'),
      ('mohamed', 'aly', 'mohamed@gmail.com'),
      ('omar', 'aly', 'omar@gmail.com'),
      ('mahmoud', 'ragab', 'mahmoud@gmail.com'),
      ('mohamed', 'ragab', 'mragab@gmail.com'),
      ('ahmed', 'hassan', 'ahmed@gmail.com');
```
- Let's run simple queries using DDL :
  - Using `Select Statement` :

```
select * from clients;
select first_name, last_name from clients;
select first_name, last_name from clients where id=3;
select first_name, last_name from clients where id between 1 and 4;
select first_name, last_name from clients where id > 4;
select * from clients where first_name like 'A%'; ## Getting all first_name starting with 'A'
select * from clients where first_name not like 'A%'; ## The Opposite of like
select * from clients where first_name like '____'; ## It is 4x"_" which means select all contains 4 letters or digits.
select distinct first_name from clients; ## This will remove any duplication.
select concat(first_name ,' ', last_name) AS 'Name' from clients; ## Grouping two rows into one column
select concat(first_name, ' ', last_name) AS "Full Name" from clients order by last_name;
select first_name from clients limit 3; ## Limiting only to 3 results "The first 3 rows only"
```

 - Using `Alter` :

```
alter table clients add city VARVHAR(50); ## Adding aditional column
alter table clients remove city; ## Removing a column
alter table clients modify city varchar(100) ## Modifying the data type of a column
```

 - Using `Update` :
```
update clients set city = 'London' where id=4;
```
 - Using `Delete` :
```
delete from clients where id =5;
```