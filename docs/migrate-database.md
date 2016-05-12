# migrate database

*Migration is the process of copying the schema objects and data from a source third-party (non-Oracle) database, such as MySQL, Microsoft SQL Server, Sybase Adaptive Server, or Microsoft Access, to an Oracle database. You can perform the migration in an efficient, largely automated way. Thus, you have two options for working with third-party databases in SQL Developer: 1. Creating database connections so that you can view schema objects and data in these databases. 2. Migrating these databases to Oracle, to take advantage of the full range of Oracle Database features and capabilities.* (https://docs.oracle.com/cd/E11882_01/doc.112/e12152/migration.htm)

## References
* https://docs.oracle.com/cd/E11882_01/doc.112/e12152/migration.htm
* https://www.youtube.com/watch?v=W1QaEHpNw6Y
* https://www.youtube.com/watch?v=3sX6YwvwS9M
* https://www.youtube.com/watch?v=db1d1uJfQ9Q
* https://www.youtube.com/watch?v=Q9-sSHRT7n0&list=PL8SiaeRh_5oa8sUKX_W8u3mgzPiHVZEDj

##### Connect to system

##### Look under Other Users to see the names of schemas which have already been created
* Connections > System > Other Users

##### Create new schema for migration repository
###### Via command line
* Right-click the connection name and choose Open SQL Worksheet
* Issue the command: 
```
asdf
```
###### Via SQL Developer
* Right-click the Other Users node in the Connections navigator under that connection.
* Select Create User, and specify the necessary information.
  * (Under System Privileges, grant ALTER SESSION, CREATE SESSION, CREATE DATABASE LINK, CREATE MATERIALIZED VIEW, CREATE PROCEDURE, CREATE PUBLIC SYNONYM, CREATE ROLE, CREATE SEQUENCE, CREATE SYNONYM, CREATE TABLE, CREATE TRIGGER, CREATE TYPE, CREATE VIEW, and UNLIMITED TABLESPACE.)

##### Grant privledges to migration repository schema
##### Connect to migration repository schema
##### Associate migration repository
##### Migrate to Oracle



