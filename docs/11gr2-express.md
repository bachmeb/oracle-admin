# oracle db 11g release 2

## References
* http://docs.oracle.com/cd/E17781_01/install.112/e18802/toc.htm#XEINL101

### Requirements
* Operating system
   * One of the following:
      * Oracle Enterprise Linux 4 Update 7
      * Oracle Enterprise Linux 5 Update 2
      * Red Hat Enterprise Linux 4 Update 7
      * Red Hat Enterprise Linux 5 Update 2
      * SUSE Linux Enterprise Server 10 SP2
      * SUSE Linux Enterprise Server 11
* RAM
  * 256 megabytes minimum, 512 megabytes recommended
* Disk space
  * 1.5 gigabyte minimum
* Packages
  * glibc should be greater than or equal to 2.3.4-2.41
  * make should be greater than or equal to 3.80
  * binutils should be greater than or equal to 2.16.91.0.5
  * gcc should be greater than or equal to 4.1.2
  * libaio should be greater than or equal to 0.3.104
* Swap
  * Minimum swap space required for Oracle Database XE is 2 GB or twice the size of RAM, whichever is lesser.
* Kernel
  * The Oracle Database XE installation checks your system for the following kernel parameter settings. If the kernel parameters of your system are less than the values listed in Table 2, then the installation will modify the kernel parameter setting to use these values.
    * semmsl  250
    * semmns  32000
    * semopm  100
    * semmni  128
    * shmmax  4294967295
    * shmmni  4096
    * shmall  2097152
    * file-max  6815744
    * VERSION 2.4.21
    * ip_local_port_range 9000–65500
* Permission
  * You must have root permission to install Oracle Database XE.
### Limitations
* Data
  * The maximum amount of user data in an Oracle Database XE database cannot exceed 11 gigabytes. If the user data grows beyond this limit, then an ORA-12592 error will appear. To use more than 11 gigabytes of user data, upgrade to Oracle Database 11g Standard Edition, Oracle Database 11g Standard Edition One, or Oracle Database 11g Enterprise Edition.
* RAM
  * The maximum amount of RAM that an Oracle Database XE database uses cannot exceed 1 gigabyte, even if more is available. 
  * Table 1, "Oracle Database XE Requirements" provides the minimum and recommended RAM that you should use. 
  * The exact amount of RAM that Oracle Database XE uses is computed automatically using Automatic Memory Management.

To use more than 1 gigabyte of RAM, upgrade to Oracle Database 11g Standard Edition, Oracle Database 11g Standard Edition One, or Oracle Database 11g Enterprise Edition.

##### Download Oracle Database Express Edition 11g Release 2 for Linux x64
* http://www.oracle.com/technetwork/database/database-technologies/express-edition/downloads/index.html

##### Copy the install file to the target machine
```
scp oracle-xe-11.2.0-1.0.x86_64.rpm.zip [username]@[hostname]:~/Downloads
```

##### Connect to the target machine
```
ssh username@hostname
```

##### Make a new directory
```
mkdir ~/Downloads/oxe
```

##### Put the installation file in the new directory
```
mv ~/Downloads/oracle-xe-11.2.0-1.0.x86_64.rpm.zip ~/Downloads/oxe
```

##### Unzip the installation file
```
cd ~/Downloads/oxe
unzip oracle-xe-11.2.0-1.0.x86_64.rpm.zip 
```
```c
/*
Archive:  oracle-xe-11.2.0-1.0.x86_64.rpm.zip
   creating: Disk1/
   creating: Disk1/upgrade/
  inflating: Disk1/upgrade/gen_inst.sql  
   creating: Disk1/response/
  inflating: Disk1/response/xe.rsp   
  inflating: Disk1/oracle-xe-11.2.0-1.0.x86_64.rpm  
*/
```

##### Change to the Disk1 directory
```
cd Disk1/
```

##### List the contents of the directory
```
ls
```
```c
/*
total 309892
-rw-rw-r--. 1 bachmeb bachmeb 317320273 Aug 29  2011 oracle-xe-11.2.0-1.0.x86_64.rpm
drwxr-xr-x. 2 bachmeb bachmeb      4096 Aug 29  2011 response
drwxrwxr-x. 2 bachmeb bachmeb      4096 Aug 29  2011 upgrade
*/
```

##### Run the Oracle installer
```
sudo rpm -ivh oracle-xe-11.2.0-1.0.x86_64.rpm 
```
```c
/*
Preparing...                ########################################### [100%]
   1:oracle-xe              ########################################### [100%]
Executing post-install steps...

You must run '/etc/init.d/oracle-xe configure' as the root user to configure the database.
*/
```

##### Run oracle-xe configure 
```
sudo /etc/init.d/oracle-xe configure
```
```c
/*

Oracle Database 11g Express Edition Configuration
-------------------------------------------------
This will configure on-boot properties of Oracle Database 11g Express 
Edition.  The following questions will determine whether the database should 
be starting upon system boot, the ports it will use, and the passwords that 
will be used for database accounts.  Press <Enter> to accept the defaults. 
Ctrl-C will abort.

Specify the HTTP port that will be used for Oracle Application Express [8080]:8888

Specify a port that will be used for the database listener [1521]:

Specify a password to be used for database accounts.  Note that the same
password will be used for SYS and SYSTEM.  Oracle recommends the use of 
different passwords for each database account.  This can be done after 
initial configuration:
The password you entered contains invalid characters. Enter password:
The password you entered contains invalid characters. Enter password:
Confirm the password:

Do you want Oracle Database 11g Express Edition to be started on boot (y/n) [y]:n

Starting Oracle Net Listener...Done
Configuring database...Done
Starting Oracle Database 11g Express Edition instance...Done
Installation completed successfully.
*/
```

##### Check the status of the oracle-xe service
```
sudo /sbin/service oracle-xe status
```
```c
/*
LSNRCTL for Linux: Version 11.2.0.2.0 - Production on 10-MAY-2016 16:39:25

Copyright (c) 1991, 2011, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))
STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 11.2.0.2.0 - Production
Start Date                10-MAY-2016 16:34:42
Uptime                    0 days 0 hr. 4 min. 45 sec
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

##### Start the oracle-xe service
```
sudo /sbin/service oracle-xe start
```
```c
/*
Starting Oracle Net Listener.
Starting Oracle Database 11g Express Edition instance.
*/
```

##### Go to the xe/bin directory
```
cd /u01/app/oracle/product/11.2.0/xe/bin
```

##### Read the oracle_env bash script
```
less oracle_env.sh
```
```bash
export ORACLE_HOME=/u01/app/oracle/product/11.2.0/xe
export ORACLE_SID=XE
export NLS_LANG=`$ORACLE_HOME/bin/nls_lang.sh`
export PATH=$ORACLE_HOME/bin:$PATH
```

##### Run the bash script to configure your environment variables
```
bash -x ./oracle_env.sh 
```
```
/*
+ export ORACLE_HOME=/u01/app/oracle/product/11.2.0/xe
+ ORACLE_HOME=/u01/app/oracle/product/11.2.0/xe
+ export ORACLE_SID=XE
+ ORACLE_SID=XE
++ /u01/app/oracle/product/11.2.0/xe/bin/nls_lang.sh
+ export NLS_LANG=AMERICAN_AMERICA.AL32UTF8
+ NLS_LANG=AMERICAN_AMERICA.AL32UTF8
+ export PATH=/u01/app/oracle/product/11.2.0/xe/bin:/usr/lib64/qt-3.3/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/bachmeb/bin
+ PATH=/u01/app/oracle/product/11.2.0/xe/bin:/usr/lib64/qt-3.3/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/bachmeb/bin
*/
```
