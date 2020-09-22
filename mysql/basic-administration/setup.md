#### We will setup MySQL using Docker

```
docker run -d --name mysql -e MYSQL_ROOT_PASSWORD=Password -p 0.0.0.0:3306:3306 -d mysql:latest
```

#### Create a Database

```
mysql -u root -p
CREATE DATABASE my_db
```

#### Database permissions 
```
CREATE USER 'aly'@'localhost' IDENTIFIED BY 'password123';
```
#### This will allow the user to only connect to the database , so let's create a permissions 
```
GRANT INSERT, SELECT, UPDATE ON my_db TO 'aly'@'localhost';
```
#### If we need to give a user all permissions on a database so it will be
```
GRANT ALL PRIVILEGES ON my_db TO 'aly'@'localhost';
```
#### If we need to set a permissions to user on specific table
```
GRANT UPDATE, SELECT ON my_db.my_table TO 'aly'@'localhost';
```
#### To allow all accesses to all databases :
```
GRANT ALL PRIVILEGES ON *.* TO 'aly'@'localhost';
```
#### To display all permissions
```
SHOW GRANTS FOR 'aly'@'localhost';
```
##### To Revoke update and select or all privileges from a user 
```
REVOKE UPDATE, SELECT ON my_db.* FROM 'aly'@'localhost';
REVOKE ALL PRIVILEGES ON my_db.* FROM 'aly'@'localhost';
```
#### To Remove the user 
```
DROP USER 'aly'@'localhost'
```