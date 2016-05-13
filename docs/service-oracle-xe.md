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

##### Check the status of the oracle-xe service (running)
```
sudo /sbin/service oracle-xe status
```
```c
/*
LSNRCTL for Linux: Version 11.2.0.2.0 - Production on 13-MAY-2016 11:28:53

Copyright (c) 1991, 2011, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 11.2.0.2.0 - Production
Start Date                13-MAY-2016 11:24:26
Uptime                    0 days 0 hr. 4 min. 27 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Default Service           XE
Listener Parameter File   /u01/app/oracle/product/11.2.0/xe/network/admin/listener.ora
Listener Log File         /u01/app/oracle/diag/tnslsnr/99700hlzx6g1/listener/alert/log.xml
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=localhost)(PORT=1521)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=localhost)(PORT=8888))(Presentation=HTTP)(Session=RAW))
Services Summary...
Service "PLSExtProc" has 1 instance(s).
  Instance "PLSExtProc", status UNKNOWN, has 1 handler(s) for this service...
Service "XE" has 1 instance(s).
  Instance "XE", status READY, has 1 handler(s) for this service...
Service "XEXDB" has 1 instance(s).
  Instance "XE", status READY, has 1 handler(s) for this service...
The command completed successfully
*/
```

##### Stop the oracle-xe service
```
sudo /sbin/service oracle-xe stop
```
```c
/*
Shutting down Oracle Database 11g Express Edition instance.
Stopping Oracle Net Listener.
*/
```
