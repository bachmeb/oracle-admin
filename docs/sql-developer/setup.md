# oracle sql developer

## References
* http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html
* https://docs.oracle.com/cd/E17781_01/server.112/e18804/dbconfig.htm#ADMQS254
* http://www.oracle.com/technetwork/developer-tools/sql-developer/mysql-connection-viewlet-swf-085075.html
* https://dev.mysql.com/downloads/connector/j/5.0.html
* http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/sqldev-install-linux-1969676.html

### Prepare

##### Install JDK 1.8
* https://github.com/bachmeb/java-jdk

### Download
* http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html

##### Windows
* Download Version 4.2+ for Windows 32-bit/64-bit (314 MB)

##### Linux
* Download Version 4.2+ for Linux RPM (308 MB)

### Install

##### Install (CentoOS 6.7)
* rpm -Uhv sqldeveloper-(build number)-1.noarch.rpm (install the package)
* cd /opt/sqldeveloper (go to sqldeveloper folder)
* ./sqldeveloper.sh (run sqldeveloper.sh file)
* You will be prompted to enter a jdk path. (ie /usr/lib/jvm/java-1.8.0)
* SQL Developer will automatically launch once jdk location is provided

### Connect

##### Connect to MySQL DB on a remote host
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

##### Connect to Oracle XE on a remote host
* View > Connections
  * Click New Connection
    * Connnection name: OracleXE
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

##### Connect to Oracle XE on localhost
* View > Connections
  * Click New Connection
    * Connnection name:
    * Username: 
    * Password: 
    * Save password: YES
    * Oracle tab
      * Connection type: Basic
      * Role: default
      * Hostname: 127.0.0.1
      * Port: 1521
      * SID: xe
      * OS Authentication: NO
      * Kerebos Authentication: NO
      * Proxy Connection: NO
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
