# Create a database user
* *You should create at least one database user that you will use to create database objects. A database user is a type of database object: a user is associated with a database schema, you connect to the database as a database user, and the database user is the owner of any database objects (tables and so on) that you create in the schema associated with the user.* (https://docs.oracle.com/cd/E17781_01/admin.112/e18585/toc.htm#XEGSG109)

##### Run the SQL Command Line
* Applications > Oracle Database > Run SQL Command Line

```c
/*
SQL*Plus: Release 11.2.0.2.0 Production on Wed May 11 11:52:12 2016

Copyright (c) 1982, 2011, Oracle.  All rights reserved.

Use "connect username/password@XE" to connect to the database.
SQL> 
*/
```

##### Connect
```
SQL> connect
Enter user-name: system
Enter password: <password-for-system>
Connected.
```

##### Create the user
```sql
SQL> create user brian identified by <password for brian>;
```
```
User created
```

##### Grant the user the necessary privileges
```
SQL> grant CREATE SESSION, ALTER SESSION, CREATE DATABASE LINK, -
  CREATE MATERIALIZED VIEW, CREATE PROCEDURE, CREATE PUBLIC SYNONYM, -
  CREATE ROLE, CREATE SEQUENCE, CREATE SYNONYM, CREATE TABLE, - 
  CREATE TRIGGER, CREATE TYPE, CREATE VIEW, UNLIMITED TABLESPACE -
  to brian;
```

