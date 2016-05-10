# oracle sql developer

## References
* http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html
* https://docs.oracle.com/cd/E17781_01/server.112/e18804/dbconfig.htm#ADMQS254

##### Download Version 4.1.3.20.78, Updated December 22, 2015
* http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html

##### Determine the DB version using the Reports view
* Click the Reports tab on the left, near the Connections navigator. (If this tab is not visible, click View, then Reports.)
* In the Reports navigator, expand Data Dictionary Reports.
* Under Data Dictionary Reports, expand About Your Database.
* Under About Your Database, click Version Banner.

##### Query for the db version
```
select * from v$version;
```
