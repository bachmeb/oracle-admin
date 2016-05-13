# service oracle-xe 

##### Check the status of the oracle-xe service (not running)
```
sudo /sbin/service oracle-xe status
```
```c
/*
LSNRCTL for Linux: Version 11.2.0.2.0 - Production on 13-MAY-2016 11:24:00

Copyright (c) 1991, 2011, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
TNS-12541: TNS:no listener
 TNS-12560: TNS:protocol adapter error
  TNS-00511: No listener
   Linux Error: 2: No such file or directory
Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=99700hlzx6g1)(PORT=1521)))
TNS-12541: TNS:no listener
 TNS-12560: TNS:protocol adapter error
  TNS-00511: No listener
   Linux Error: 111: Connection refused
*/
```

##### Start oracle-xe 
```
sudo /sbin/service oracle-xe start
```
```c
/*
Starting Oracle Net Listener.
Starting Oracle Database 11g Express Edition instance.
*/
```
