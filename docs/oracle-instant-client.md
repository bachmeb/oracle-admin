# Oracle Instant Client

## References
* http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html
* http://www.hexblot.com/blog/making-connection-php-oracle-centos-64

##### Download the basic and devel packages
* http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html

##### List the files in the RPM files
```
rpm -qpl oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm 
```
```c
/*
/usr/lib/oracle/12.1/client64/bin/adrci
/usr/lib/oracle/12.1/client64/bin/genezi
/usr/lib/oracle/12.1/client64/lib/libclntsh.so.12.1
/usr/lib/oracle/12.1/client64/lib/libclntshcore.so.12.1
/usr/lib/oracle/12.1/client64/lib/libipc1.so
/usr/lib/oracle/12.1/client64/lib/libmql1.so
/usr/lib/oracle/12.1/client64/lib/libnnz12.so
/usr/lib/oracle/12.1/client64/lib/libocci.so.12.1
/usr/lib/oracle/12.1/client64/lib/libociei.so
/usr/lib/oracle/12.1/client64/lib/libocijdbc12.so
/usr/lib/oracle/12.1/client64/lib/libons.so
/usr/lib/oracle/12.1/client64/lib/liboramysql12.so
/usr/lib/oracle/12.1/client64/lib/ojdbc6.jar
/usr/lib/oracle/12.1/client64/lib/ojdbc7.jar
/usr/lib/oracle/12.1/client64/lib/xstreams.jar
*/
```
```
rpm -qpl oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm 
```
```c
/*
/usr/include/oracle/12.1/client64/ldap.h
/usr/include/oracle/12.1/client64/nzerror.h
/usr/include/oracle/12.1/client64/nzt.h
/usr/include/oracle/12.1/client64/occi.h
/usr/include/oracle/12.1/client64/occiAQ.h
/usr/include/oracle/12.1/client64/occiCommon.h
/usr/include/oracle/12.1/client64/occiControl.h
/usr/include/oracle/12.1/client64/occiData.h
/usr/include/oracle/12.1/client64/occiObjects.h
/usr/include/oracle/12.1/client64/oci.h
/usr/include/oracle/12.1/client64/oci1.h
/usr/include/oracle/12.1/client64/oci8dp.h
/usr/include/oracle/12.1/client64/ociap.h
/usr/include/oracle/12.1/client64/ociapr.h
/usr/include/oracle/12.1/client64/ocidef.h
/usr/include/oracle/12.1/client64/ocidem.h
/usr/include/oracle/12.1/client64/ocidfn.h
/usr/include/oracle/12.1/client64/ociextp.h
/usr/include/oracle/12.1/client64/ocikpr.h
/usr/include/oracle/12.1/client64/ocixmldb.h
/usr/include/oracle/12.1/client64/ocixstream.h
/usr/include/oracle/12.1/client64/odci.h
/usr/include/oracle/12.1/client64/oratypes.h
/usr/include/oracle/12.1/client64/ori.h
/usr/include/oracle/12.1/client64/orid.h
/usr/include/oracle/12.1/client64/orl.h
/usr/include/oracle/12.1/client64/oro.h
/usr/include/oracle/12.1/client64/ort.h
/usr/include/oracle/12.1/client64/xa.h
/usr/lib/oracle/12.1/client64/lib/libclntsh.so
/usr/lib/oracle/12.1/client64/lib/libclntshcore.so
/usr/lib/oracle/12.1/client64/lib/libocci.so
/usr/lib/oracle/12.1/client64/lib/ottclasses.zip
/usr/share/oracle/12.1/client64/admin/oraaccess.xsd
/usr/share/oracle/12.1/client64/demo/cdemo81.c
/usr/share/oracle/12.1/client64/demo/demo.mk
/usr/share/oracle/12.1/client64/demo/occidemo.sql
/usr/share/oracle/12.1/client64/demo/occidemod.sql
/usr/share/oracle/12.1/client64/demo/occidml.cpp
/usr/share/oracle/12.1/client64/demo/occiobj.cpp
/usr/share/oracle/12.1/client64/demo/occiobj.typ
/usr/share/oracle/12.1/client64/demo/oraaccess.xml
/usr/share/oracle/12.1/client64/demo/ott
/usr/share/oracle/12.1/client64/demo/setuporamysql.sh
*/
```

##### Install the basic package
```
sudo rpm -ivh oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm 
```
```c
/*
Preparing...                ########################################### [100%]
   1:oracle-instantclient12.########################################### [100%]
*/
```

##### Install the devel package
```
sudo rpm -ivh oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm 
```
```c
/*
Preparing...                ########################################### [100%]
   1:oracle-instantclient12.########################################### [100%]
*/
```

##### Find the client64 directories
```
sudo find / -name client64
```
```c
/*
/usr/include/oracle/12.1/client64
/usr/share/oracle/12.1/client64
/usr/lib/oracle/12.1/client64
*/
```

##### List the contents of the client64/lib directory
```
ls /usr/lib/oracle/12.1/client64/lib/
```
```c
/*
libclntshcore.so       libclntsh.so.12.1  libnnz12.so      libociei.so      liboramysql12.so  ottclasses.zip
libclntshcore.so.12.1  libipc1.so         libocci.so       libocijdbc12.so  ojdbc6.jar        xstreams.jar
libclntsh.so           libmql1.so         libocci.so.12.1  libons.so        ojdbc7.jar
*/
```

##### List the contents of the ld.so.conf.d directory
```
ls /etc/ld.so.conf.d/
```
```c
/*
kernel-2.6.32-573.26.1.el6.x86_64.conf  mysql57u-x86_64.conf                    qt-x86_64.conf
kernel-2.6.32-573.el6.x86_64.conf       mysqlclient16-x86_64.conf               xulrunner-64.conf
*/
```

##### Create an Oracle Client config file
```
sudo nano /etc/ld.so.conf.d/oracle_client.conf
```

##### Add the path to the lib directory to the config file
```
/usr/lib/oracle/12.1/client64/lib/
```

##### Check the current value of LD_LIBRARY_PATH
```
echo $LD_LIBRARY_PATH
```

##### Set the environment variable LD_LIBRARY_PATH to the appropriate directory for the Instant Client version
```
export LD_LIBRARY_PATH=/usr/lib/oracle/12.1/client64/lib:$LD_LIBRARY_PATH
```

##### Check the current value of LD_LIBRARY_PATH
```
echo $LD_LIBRARY_PATH
```

