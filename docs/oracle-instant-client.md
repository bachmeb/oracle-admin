# Oracle Instant Client

## References
* http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html

##### Download the basic and devel packages
* http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html

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

##### Find where client64 was installed
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
