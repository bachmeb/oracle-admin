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
