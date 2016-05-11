# oracle sql developer

## References
* http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html
* https://docs.oracle.com/cd/E17781_01/server.112/e18804/dbconfig.htm#ADMQS254
* http://www.oracle.com/technetwork/developer-tools/sql-developer/mysql-connection-viewlet-swf-085075.html
* https://dev.mysql.com/downloads/connector/j/5.0.html

### Download

##### Download Version 4.1.3.20.78, Updated December 22, 2015
* http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html

### Install

##### Install (CentoOS 6.7)

### Connect

##### Connect to MySQL DB
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
    * Connnection name:
    * Username: 
    * Password: 
    * Save password: YES
    * MySQL tab
      * Hostname: [target database hostname or IP address]
      * Port: 3306
      * Click Choose Database
      * Select a database from the dropdown menu
      * Click Test
        * *Look for Status: Success*
      * Click Connect to save the connection

##### Connect to Oracle XE on localhost
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
    * Connnection name:
    * Username: 
    * Password: 
    * Save password: YES
    * MySQL tab
      * Hostname: [target database hostname or IP address]
      * Port: 3306
      * Click Choose Database
      * Select a database from the dropdown menu
      * Click Test
        * *Look for Status: Success*
      * Click Connect to save the connection

### Admin

##### Determine the DB version using the Reports view
* Click the Reports tab on the left, near the Connections navigator. (If this tab is not visible, click View, then Reports.)
* In the Reports navigator, expand Data Dictionary Reports.
* Under Data Dictionary Reports, expand About Your Database.
* Under About Your Database, click Version Banner.

### Query

##### Query for the db version
```
select * from v$version;
```
