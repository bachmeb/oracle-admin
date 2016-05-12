# migrate database

*Migration is the process of copying the schema objects and data from a source third-party (non-Oracle) database, such as MySQL, Microsoft SQL Server, Sybase Adaptive Server, or Microsoft Access, to an Oracle database. You can perform the migration in an efficient, largely automated way. Thus, you have two options for working with third-party databases in SQL Developer: 1. Creating database connections so that you can view schema objects and data in these databases. 2. Migrating these databases to Oracle, to take advantage of the full range of Oracle Database features and capabilities.* (https://docs.oracle.com/cd/E11882_01/doc.112/e12152/migration.htm)

## References
* https://docs.oracle.com/cd/E11882_01/doc.112/e12152/migration.htm
* https://www.youtube.com/watch?v=W1QaEHpNw6Y
* https://www.youtube.com/watch?v=3sX6YwvwS9M
* https://www.youtube.com/watch?v=db1d1uJfQ9Q
* https://www.youtube.com/watch?v=Q9-sSHRT7n0&list=PL8SiaeRh_5oa8sUKX_W8u3mgzPiHVZEDj

##### Connect to system
* View > Connections
  * Click New Connection
    * Connnection name: xe-system
    * Username: SYSTEM
    * Password: [ -- enter the password for the SYSTEM account -- ]
    * Save password: YES
    * Oracle tab
      * Connection type: Basic
      * Role: default
      * Hostname: [target database hostname or IP address]
      * Port: 1521
      * SID: xe
      * OS Authentication: NO
      * Kerebos Authentication: NO
      * Proxy Connection: NO
      * Click Test
        * *Look for Status: Success*
      * Click Connect to save the connection

##### Look under Other Users to see the names of schemas which have already been created
* Connections > xe-system > Other Users

##### Create new schema for migration repository
###### Via command line
* Right-click the connection name and choose Open SQL Worksheet
* Issue the command: 
```sql
-- USER SQL
CREATE USER migrator IDENTIFIED BY migrator 
DEFAULT TABLESPACE "USERS"
TEMPORARY TABLESPACE "TEMP";

-- QUOTAS

-- ROLES
GRANT "RESOURCE" TO migrator WITH ADMIN OPTION;

-- SYSTEM PRIVILEGES
GRANT CREATE USER TO migrator WITH ADMIN OPTION;
GRANT ALTER ANY TABLE TO migrator WITH ADMIN OPTION;
GRANT CREATE VIEW TO migrator ;
GRANT CREATE ROLE TO migrator WITH ADMIN OPTION;
GRANT CREATE SESSION TO migrator ;
```
###### Via SQL Developer
* Right-click the Other Users node in the Connections navigator under that connection.
* Select Create User
  * User
    * User Name: migrator
    * New Password: [ -- whatever -- ]
    * Password Expired: NO
    * Account is Locked: NO
    * Edition Enabled: NO
    * Default Tablespace: USER
    * Temporary Tablespace: TEMP
  * Granted Roles
    * RESOURCE (Granted, Admin)
  * System Privileges
    * ALTER ANY TRIGGER (Granted, Admin Option)
    * CREATE ROLE (Granted, Admin Option)
    * CREATE SESSION (Granted)
    * CREATE USER (Granted, Admin)
    * CREATE VIEW (Granted)
  * Quotas
    * SYSAUX	false
    * SYSTEM	false
    * TEMP	false
    * UNDOTBS1	false
    * USERS	false		

##### Connect to migration repository schema
* View > Connections
  * Click New Connection
    * Connnection name: xe-migrator
    * Username: migrator
    * Password: [ -- enter the password for the migrator account -- ]
    * Save password: YES
    * Oracle tab
      * Connection type: Basic
      * Role: default
      * Hostname: [target database hostname or IP address]
      * Port: 1521
      * SID: xe
      * OS Authentication: NO
      * Kerebos Authentication: NO
      * Proxy Connection: NO
      * Click Test
        * *Look for Status: Success*
      * Click Connect to save the connection

##### Associate migration repository
* Right click the xe-migrator connection
* Choose Migration Repository > Associate Migration Repository


##### Create a connection to source database (in this example, the database is a MySQL DB)
* Download a copy of the MySQL connector
  * [sql-developer](/docs/sql-developer.md)
* Tools > Preferences
  * Database
    * Third Party JDBC Driver
      * Click Add Entry
        * Select the jar file: mysql-connector-java-5.0.4-bin.jar
      * Click OK
* View > Connections
  * Click New Connection
    * Connnection name: migration-source
    * Username: [ source db username]
    * Password: [ source db password ]
    * Save password: YES
    * MySQL tab
      * Hostname: [target database hostname or IP address]
      * Port: 3306
      * Click Choose Database
      * Select a database from the dropdown menu
      * Click Test
        * *Look for Status: Success*
      * Click Connect to save the connection

##### Migrate database
* Right click the migration-source connection
* Select Migrate to Oracle
  * Migration Wizard
    * Introduction
      * Next
    * Repository
      * Connection: xe-migrator
      * Truncate: NO
    * Project
      * Name: whatever
      * Output Directory: wherever
    * Source Database
      * Mode: Online
      * Connection: migration-source
    * Capture
      * Available Databases
        * [ This list should have at least one db ]
      * Selected Databases
        * [ Move the databases you want to move into this list ]
    * Convert
      * [ Review the proposed data type mappings ]
    * Translate
      * Available SQL Objects
        * [ should be blank ]
      * Selected SQL Objects
        * ALL_CONSTRAINTS
        * ALL_FUNCTIONS
        * ALL_PROCEDURES
        * ALL_TRIGGERS
        * ALL_VIEWS
    * Target Database
      * Mode: Online
      * Connection: xe-system
      * Drop Target Objects: NO
    * Move Data
      * Mode: Online
      * Source: migration-source
      * Target: xe-system
      * Truncate Data: NO
    * Summary
      * Finish

##### Confirm migrated data
* Go to the xe-system connection
* Expand Other Users
* Look for the databases selected on the Capture screen of the migration wizard to appears as new users

##### Connect to the migrated database
* View > Connections
  * Click New Connection
    * Connnection name: xe-migrated
    * Username: SYSTEM
    * Password: [ -- enter the SYSTEM password -- ]
    * Save password: YES
    * Oracle tab
      * Connection type: Basic
      * Role: default
      * Hostname: [target database hostname or IP address]
      * Port: 1521
      * SID: xe
      * OS Authentication: NO
      * Kerebos Authentication: NO
      * Proxy Connection: NO
      * Click Test
        * *Look for Status: Success*
      * Click Connect to save the connection

