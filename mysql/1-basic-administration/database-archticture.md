### MySQL Server Archticture 
<img src="https://github.com/AlyRagab/databases-for-devops/blob/master/mysql/images/mysql.png" />

### MySQL Logical Archticture :
1- Connection Handling Layer :
- This is the first layer which handles the client request to connect to MySQL.
- It handles the Authentication Method to the Database instance.
- Each session will have its own thread in the server process.

2- Query and Optmisation Layers :
- After the connection is openned and when the client sends a query to the server,
It is the layer of parsing , caching a query.
- The server which already caches the query "SELECT statement only" then will get the client request and check it in the 
query cache layer to check which index to use for this query.
- If the query is not in the cache then , The server parses the query and optimise it and send it to the query execution engine.
- The execution engine makes an API request to the storage engine API.

- About the Query Optimizer, It predict the cost of the execution request and chooses the least 
expensive one , the default is a random 4KB data page read, and we can check it by this query :
```
SHOW STATUS LIKE ‘Last_query_cost’;
```

3- Storage Egine Layer :
- It is the layer which responsible for 'Storing' and 'Retrieving' a Data stored in MySQL.
- When a schema "database" is created , MySQL creates a subdirectory with its name.
- When creating a table , MySQL will create a file ".frm" with the same table name 
storing in this file the table definitions and we can get all information of the table by :
```
SHOW TABLE STATUS LIKE 'my_table' \G;
```
- The storage engine can be specified at the table creation with the "Engine='' " option
To check the used storage engine :
```
SHOW ENGINES\G
```
- There are a lot of storage engines in MySQL and the below are the details :
   - MyISAM :
     - Is used when we have a Static Applications with select query and less update and insert.
     - Supports Table-Level Locking.
     - No Rollback for queries , Once command is done so you can not rollback.
     - Table size is up to 256TB

   - InnoDB :
     - Supports Row-Level Locking.
     - Supports Database Transactions as there is rollback.
     - High Performance with high volume of data.
     - Useful for Dynamic Applications.
     - Table size is up to 64TB.
     - Supports foreign key referential integrity constraint.

   - Memory :
     - Uses HEAP Memory for storing Data.
     - The Data lifetime depends on the uptime of the Database Instance.
     - It is the Fastest engine.
     - Supports table-level locking.
     - Does not support transactions , No rollback.
     - Useful for any temporary operations.