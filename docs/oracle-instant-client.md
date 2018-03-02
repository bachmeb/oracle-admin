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
##### Register the newly installed libraries
```
sudo ldconfig -v
```
```c
/*
ldconfig: /etc/ld.so.conf.d/kernel-2.6.32-573.el6.x86_64.conf:6: duplicate hwcap 1 nosegneg
ldconfig: Path `/usr/lib64/mysql' given more than once
/usr/lib64/mysql:
	libmysqlclient_r.so.16 -> libmysqlclient_r.so.16.0.0
	libmysqlclient.so.16 -> libmysqlclient.so.16.0.0
	libmysqlclient.so.1020 -> libmysqlclient.so.1020.2.1
/usr/lib/oracle/12.1/client64/lib:
	libnnz12.so -> libnnz12.so
	libipc1.so -> libipc1.so
	libmql1.so -> libmql1.so
	liboramysql12.so -> liboramysql12.so
	libons.so -> libons.so
	libocijdbc12.so -> libocijdbc12.so
	libocci.so.12.1 -> libocci.so.12.1
	libclntshcore.so.12.1 -> libclntshcore.so.12.1
	libociei.so -> libociei.so
	libclntsh.so.12.1 -> libclntsh.so.12.1
/usr/lib64/qt-3.3/lib:
	libqt-mt.so.3 -> libqt-mt.so.3.3.8
	libqui.so.1 -> libqui.so.1.0.0
/usr/lib64/xulrunner:
	libxpcom.so -> libxpcom.so
	libxul.so -> libxul.so
	libmozalloc.so -> libmozalloc.so
	libmozsqlite3.so -> libmozsqlite3.so
/lib:
	libdl.so.2 -> libdl-2.12.so
	libfreebl3.so -> libfreebl3.so
	ld-linux.so.2 -> ld-2.12.so
	libpthread.so.0 -> libpthread-2.12.so
	libnss_nisplus.so.2 -> libnss_nisplus-2.12.so
	libaio.so.1.0.0 -> libaio.so.1.0.0
	libnss_dns.so.2 -> libnss_dns-2.12.so
	libm.so.6 -> libm-2.12.so
	libBrokenLocale.so.1 -> libBrokenLocale-2.12.so
	libnss_files.so.2 -> libnss_files-2.12.so
	librt.so.1 -> librt-2.12.so
	libutil.so.1 -> libutil-2.12.so
	libthread_db.so.1 -> libthread_db-1.0.so
	libnsl.so.1 -> libnsl-2.12.so
	libanl.so.1 -> libanl-2.12.so
	libfreeblpriv3.so -> libfreeblpriv3.so
	libresolv.so.2 -> libresolv-2.12.so
	libSegFault.so -> libSegFault.so
	libnss_hesiod.so.2 -> libnss_hesiod-2.12.so
	libc.so.6 -> libc-2.12.so
	libnss_nis.so.2 -> libnss_nis-2.12.so
	libgcc_s.so.1 -> libgcc_s-4.4.7-20120601.so.1
	libaio.so.1 -> libaio.so.1.0.1
	libcidn.so.1 -> libcidn-2.12.so
	libnss_compat.so.2 -> libnss_compat-2.12.so
	libcrypt.so.1 -> libcrypt-2.12.so
/lib64:
	libplds4.so -> libplds4.so
	libdb_cxx-4.2.so -> libdb_cxx-4.2.so
	libsemanage.so.1 -> libsemanage.so.1
	libdevmapper.so.1.02 -> libdevmapper.so.1.02
	libgssapi_krb5.so.2 -> libgssapi_krb5.so.2.2
	libnss_wins.so.2 -> libnss_wins.so.2
	libdl.so.2 -> libdl-2.12.so
	libselinux.so.1 -> libselinux.so.1
	libply.so.2 -> libply.so.2.0.0
	liblvm2app.so.2.2 -> liblvm2app.so.2.2
	libpam.so.0 -> libpam.so.0.82.2
	libkrb5.so.3 -> libkrb5.so.3.3
	ld-linux-x86-64.so.2 -> ld-2.12.so
	libfreebl3.so -> libfreebl3.so
	libmount.so.1 -> libmount.so.1.1.0
	libdb_cxx-4.3.so -> libdb_cxx-4.3.so
	libsepol.so.1 -> libsepol.so.1
	libpthread.so.0 -> libpthread-2.12.so
	libdb-4.2.so -> libdb-4.2.so
	libnss_nisplus.so.2 -> libnss_nisplus-2.12.so
	libply-splash-core.so.2 -> libply-splash-core.so.2.0.0
	libaio.so.1.0.0 -> libaio.so.1.0.0
	libfipscheck.so.1 -> libfipscheck.so.1.1.0
	libdevmapper-event-lvm2.so.2.02 -> libdevmapper-event-lvm2.so.2.02
	libgio-2.0.so.0 -> libgio-2.0.so.0.2800.8
	libblkid.so.1 -> libblkid.so.1.1.0
	libipq.so.0 -> libipq.so.0.0.0-1.4.7
	libulockmgr.so.1 -> libulockmgr.so.1.0.1
	libnspr4.so -> libnspr4.so
	libnss_dns.so.2 -> libnss_dns-2.12.so
	libm.so.6 -> libm-2.12.so
	libncursesw.so.5 -> libncursesw.so.5.7
	libBrokenLocale.so.1 -> libBrokenLocale-2.12.so
	libjson-c.so.2 -> libjson-c.so.2.0.1
	libcap-ng.so.0 -> libcap-ng.so.0.0.0
	libdb-4.7.so -> libdb-4.7.so
	libpamc.so.0 -> libpamc.so.0.82.1
	libdevmapper-event.so.1.02 -> libdevmapper-event.so.1.02
	libgssrpc.so.4 -> libgssrpc.so.4.1
	libnss_files.so.2 -> libnss_files-2.12.so
	liblvm2cmd.so.2.02 -> liblvm2cmd.so.2.02
	libasound.so.2 -> libasound.so.2.0.0
	librt.so.1 -> librt-2.12.so
	libutil.so.1 -> libutil-2.12.so
	libplc4.so -> libplc4.so
	libgthread-2.0.so.0 -> libgthread-2.0.so.0.2800.8
	libthread_db.so.1 -> libthread_db-1.0.so
	libnsl.so.1 -> libnsl-2.12.so
	libncurses.so.5 -> libncurses.so.5.7
	libnih-dbus.so.1 -> libnih-dbus.so.1.0.0
	libwrap.so.0 -> libwrap.so.0.7.6
	libattr.so.1 -> libattr.so.1.1.0
	libnl.so.1 -> libnl.so.1.1.4
	libext2fs.so.2 -> libext2fs.so.2.4
	libgcrypt.so.11 -> libgcrypt.so.11.5.3
	libaudit.so.1 -> libaudit.so.1.0.0
	libiptc.so.0 -> libiptc.so.0.0.0-1.4.7
	libidn.so.11 -> libidn.so.11.6.1
	libpci.so.3 -> libpci.so.3.1.10
	libcom_err.so.2 -> libcom_err.so.2.1
	libss.so.2 -> libss.so.2.0
	libudev.so.0 -> libudev.so.0.5.1
	libnss_winbind.so.2 -> libnss_winbind.so.2
	libanl.so.1 -> libanl-2.12.so
	libparted-2.1.so.0 -> libparted-2.1.so.0.0.0
	libip6tc.so.0 -> libip6tc.so.0.0.0-1.4.7
	libk5crypto.so.3 -> libk5crypto.so.3.1
	libldap-2.4.so.2 -> libldap-2.4.so.2.10.3
	libproc-3.2.8.so -> libproc-3.2.8.so
	libfreeblpriv3.so -> libfreeblpriv3.so
	libgobject-2.0.so.0 -> libgobject-2.0.so.0.2800.8
	libjson.so.0 -> libjson.so.0.1.0
	libkrb5support.so.0 -> libkrb5support.so.0.1
	libz.so.1 -> libz.so.1.2.3
	libxtables.so.4 -> libxtables.so.4.0.0-1.4.7
	libpam_misc.so.0 -> libpam_misc.so.0.82.0
	libreadline.so.6 -> libreadline.so.6.0
	libauparse.so.0 -> libauparse.so.0.0.0
	liblber-2.4.so.2 -> liblber-2.4.so.2.10.3
	libldap_r-2.4.so.2 -> libldap_r-2.4.so.2.10.3
	libresolv.so.2 -> libresolv-2.12.so
	libSegFault.so -> libSegFault.so
	libnss_hesiod.so.2 -> libnss_hesiod-2.12.so
	libc.so.6 -> libc-2.12.so
	libfuse.so.2 -> libfuse.so.2.8.3
	libnss_nis.so.2 -> libnss_nis-2.12.so
	libdb-4.3.so -> libdb-4.3.so
	libip4tc.so.0 -> libip4tc.so.0.0.0-1.4.7
	libpcre.so.0 -> libpcre.so.0.0.1
	libnih.so.1 -> libnih.so.1.0.0
	libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.2800.8
	libgcc_s.so.1 -> libgcc_s-4.4.7-20120601.so.1
	libbz2.so.1 -> libbz2.so.1.0.4
	libpopt.so.0 -> libpopt.so.0.0.0
	libaio.so.1 -> libaio.so.1.0.1
	libcidn.so.1 -> libcidn-2.12.so
	libkeyutils.so.1 -> libkeyutils.so.1.3
	libtinfo.so.5 -> libtinfo.so.5.7
	libldif-2.4.so.2 -> libldif-2.4.so.2.10.3
	libnss_compat.so.2 -> libnss_compat-2.12.so
	libexpat.so.1 -> libexpat.so.1.5.2
	libglib-2.0.so.0 -> libglib-2.0.so.0.2800.8
	libgpg-error.so.0 -> libgpg-error.so.0.5.0
	libuuid.so.1 -> libuuid.so.1.3.0
	libacl.so.1 -> libacl.so.1.1.0
	libdbus-1.so.3 -> libdbus-1.so.3.4.0
	libcap.so.2 -> libcap.so.2.16
	libcrypt.so.1 -> libcrypt-2.12.so
	libcryptsetup.so.1 -> libcryptsetup.so.1.1.0
	libe2p.so.2 -> libe2p.so.2.3
/usr/lib:
	libxcb-composite.so.0 -> libxcb-composite.so.0.0.0
	libX11.so.6 -> libX11.so.6.3.0
	libXi.so.6 -> libXi.so.6.1.0
	libxcb-glx.so.0 -> libxcb-glx.so.0.0.0
	libXext.so.6 -> libXext.so.6.4.0
	libxcb-shape.so.0 -> libxcb-shape.so.0.0.0
	libxcb-xtest.so.0 -> libxcb-xtest.so.0.0.0
	libelf.so.1 -> libelf-0.161.so
	libXp.so.6 -> libXp.so.6.2.0
	libxcb-screensaver.so.0 -> libxcb-screensaver.so.0.0.0
	libxcb-damage.so.0 -> libxcb-damage.so.0.0.0
	libxcb-xinerama.so.0 -> libxcb-xinerama.so.0.0.0
	libxcb-xevie.so.0 -> libxcb-xevie.so.0.0.0
	libX11-xcb.so.1 -> libX11-xcb.so.1.0.0
	libxcb-xselinux.so.0 -> libxcb-xselinux.so.0.0.0
	libxcb-dpms.so.0 -> libxcb-dpms.so.0.0.0
	libxcb-record.so.0 -> libxcb-record.so.0.0.0
	libxcb-res.so.0 -> libxcb-res.so.0.0.0
	libxcb-render.so.0 -> libxcb-render.so.0.0.0
	libxcb-xf86dri.so.0 -> libxcb-xf86dri.so.0.0.0
	libxcb-xfixes.so.0 -> libxcb-xfixes.so.0.0.0
	libxcb-xv.so.0 -> libxcb-xv.so.0.0.0
	libXtst.so.6 -> libXtst.so.6.1.0
	libstdc++.so.5 -> libstdc++.so.5.0.7
	libxcb-sync.so.0 -> libxcb-sync.so.0.0.0
	libxcb-dri2.so.0 -> libxcb-dri2.so.0.0.0
	libxcb-shm.so.0 -> libxcb-shm.so.0.0.0
	libstdc++.so.6 -> libstdc++.so.6.0.13
	libpcprofile.so -> libpcprofile.so
	libxcb-xvmc.so.0 -> libxcb-xvmc.so.0.0.0
	libmemusage.so -> libmemusage.so
	libxcb.so.1 -> libxcb.so.1.1.0
	libXau.so.6 -> libXau.so.6.0.0
	libxcb-randr.so.0 -> libxcb-randr.so.0.1.0
/usr/lib64:
	libpulsedsp.so -> libpulsedsp.so
	libhal.so.1 -> libhal.so.1.0.0
	libijs-0.35.so -> libijs-0.35.so
	libevent-1.4.so.2 -> libevent-1.4.so.2.1.3
	libhal-storage.so.1 -> libhal-storage.so.1.0.0
	libpangoft2-1.0.so.0 -> libpangoft2-1.0.so.0.2800.1
	libdevkit-power-gobject.so.1 -> libdevkit-power-gobject.so.1.0.1
	libssl3.so -> libssl3.so
	libpoppler.so.5 -> libpoppler.so.5.0.0
	libsoup-2.4.so.1 -> libsoup-2.4.so.1.4.0
	libmenuw.so.5 -> libmenuw.so.5.7
	libbfd-2.20.51.0.2-5.43.el6.so -> libbfd-2.20.51.0.2-5.43.el6.so
	libdrm_intel.so.1 -> libdrm_intel.so.1.0.0
	libORBit-imodule-2.so.0 -> libORBit-imodule-2.so.0.0.0
	libsasl2.so.2 -> libsasl2.so.2.0.23
	libnssdbm3.so -> libnssdbm3.so
	libgstnetbuffer-0.10.so.0 -> libgstnetbuffer-0.10.so.0.20.0
	libpulsecommon-0.9.21.so -> libpulsecommon-0.9.21.so
	libspeexdsp.so.1 -> libspeexdsp.so.1.5.0
	libgmpxx.so.4 -> libgmpxx.so.4.1.0
	libavahi-glib.so.1 -> libavahi-glib.so.1.0.1
	libpulse-mainloop-glib.so.0 -> libpulse-mainloop-glib.so.0.0.4
	libpolkit-backend-1.so.0 -> libpolkit-backend-1.so.0.0.0
	libdrm_nouveau2.so.2 -> libdrm_nouveau2.so.2.0.0
	libxcb-composite.so.0 -> libxcb-composite.so.0.0.0
	libaugeas.so.0 -> libaugeas.so.0.16.0
	libtasn1.so.3 -> libtasn1.so.3.1.6
	libshout.so.3 -> libshout.so.3.2.0
	libXdmcp.so.6 -> libXdmcp.so.6.0.0
	libIDL-2.so.0 -> libIDL-2.so.0.0.0
	libfam.so.0 -> libfam.so.0.0.0
	libxmlrpc_util.so.3 -> libxmlrpc_util.so.3.16
	libspeex.so.1 -> libspeex.so.1.5.0
	libcdio_cdda.so.0 -> libcdio_cdda.so.0.0.5
	libcupsppdc.so.1 -> libcupsppdc.so.1
	libX11.so.6 -> libX11.so.6.3.0
	libgstriff-0.10.so.0 -> libgstriff-0.10.so.0.20.0
	libXi.so.6 -> libXi.so.6.1.0
	libgnutlsxx.so.26 -> libgnutlsxx.so.26.14.12
	libcamel-1.2.so.19 -> libcamel-1.2.so.19.0.0
	libxcb-glx.so.0 -> libxcb-glx.so.0.0.0
	libgomp.so.1 -> libgomp.so.1.0.0
	libtheora.so.0 -> libtheora.so.0.3.9
	libchromeXvMCPro.so.1 -> libchromeXvMCPro.so.1.0.0
	libdbus-glib-1.so.2 -> libdbus-glib-1.so.2.1.0
	libfprint.so.0 -> libfprint.so.0.0.0
	libsoftokn3.so -> libsoftokn3.so
	libtag.so.1 -> libtag.so.1.6.1
	liboil-0.3.so.0 -> liboil-0.3.so.0.3.0
	libgstvideo-0.10.so.0 -> libgstvideo-0.10.so.0.20.0
	libpixman-1.so.0 -> libpixman-1.so.0.32.4
	libgdk_pixbuf_xlib-2.0.so.0 -> libgdk_pixbuf_xlib-2.0.so.0.2400.1
	libGLU.so.1 -> libGLU.so.1.3.1
	libgpgme-pth.so.11 -> libgpgme-pth.so.11.6.6
	libgstapp-0.10.so.0 -> libgstapp-0.10.so.0.20.0
	librom1394.so.0 -> librom1394.so.0.3.0
	libcupsimage.so.2 -> libcupsimage.so.2
	libpango-1.0.so.0 -> libpango-1.0.so.0.2800.1
	libXext.so.6 -> libXext.so.6.4.0
	libgamin-1.so.0 -> libgamin-1.so.0.1.10
	libgnome-bluetooth.so.7 -> libgnome-bluetooth.so.7.0.2
	libpanel.so.5 -> libpanel.so.5.7
	libcrack.so.2 -> libcrack.so.2.8.1
	libpolkit-agent-1.so.0 -> libpolkit-agent-1.so.0.0.0
	libglapi.so.0 -> libglapi.so.0.0.0
	liblcms.so.1 -> liblcms.so.1.0.19
	libiso9660.so.7 -> libiso9660.so.7.0.0
	liblua-5.1.so -> liblua-5.1.so
	libcupsmime.so.1 -> libcupsmime.so.1
	libsoup-gnome-2.4.so.1 -> libsoup-gnome-2.4.so.1.4.0
	libpangoxft-1.0.so.0 -> libpangoxft-1.0.so.0.2800.1
	libgstdataprotocol-0.10.so.0 -> libgstdataprotocol-0.10.so.0.25.0
	libgnomeui-2.so.0 -> libgnomeui-2.so.0.2400.1
	libgmp.so.3 -> libgmp.so.3.5.0
	libopenjpeg.so.2 -> libopenjpeg.so.2.1.3.0
	libpciaccess.so.0 -> libpciaccess.so.0.11.1
	libnss3.so -> libnss3.so
	libQtNetwork.so.4 -> libQtNetwork.so.4.6.2
	libgstcontroller-0.10.so.0 -> libgstcontroller-0.10.so.0.25.0
	libgstnet-0.10.so.0 -> libgstnet-0.10.so.0.25.0
	libtevent.so.0 -> libtevent.so.0.9.26
	libnsssysinit.so -> libnsssysinit.so
	libestools.so.1.2.96.1 -> libestools.so.1.2.96.1
	liblzma.so.0 -> liblzma.so.0.0.0
	libebook-1.2.so.10 -> libebook-1.2.so.10.3.1
	libmagic.so.1 -> libmagic.so.1.0.0
	libQtAssistantClient.so.4 -> libQtAssistantClient.so.4.6.2
	librpmbuild.so.1 -> librpmbuild.so.1.0.0
	libwbclient.so.0 -> libwbclient.so.0
	libtheoradec.so.1 -> libtheoradec.so.1.1.3
	libXRes.so.1 -> libXRes.so.1.0.0
	libestbase.so.1.2.96.1 -> libestbase.so.1.2.96.1
	libXxf86misc.so.1 -> libXxf86misc.so.1.1.0
	libORBit-2.so.0 -> libORBit-2.so.0.1.0
	libtar.so.1 -> libtar.so.1.2.11
	libFLAC.so.8 -> libFLAC.so.8.2.0
	libungif.so.4 -> libungif.so.4.1.6
	liblzo2.so.2 -> liblzo2.so.2.0.0
	libpolkit-gtk-1.so.0 -> libpolkit-gtk-1.so.0.0.0
	libXcomposite.so.1 -> libXcomposite.so.1.0.0
	libgpgme-pthread.so.11 -> libgpgme-pthread.so.11.6.6
	libmenu.so.5 -> libmenu.so.5.7
	libply-boot-client.so.2 -> libply-boot-client.so.2.0.0
	libgstrtp-0.10.so.0 -> libgstrtp-0.10.so.0.20.0
	libnssutil3.so -> libnssutil3.so
	libxcb-shape.so.0 -> libxcb-shape.so.0.0.0
	libedata-book-1.2.so.8 -> libedata-book-1.2.so.8.0.0
	libpython2.6.so.1.0 -> libpython2.6.so.1.0
	libtiff.so.3 -> libtiff.so.3.9.4
	libxcb-xtest.so.0 -> libxcb-xtest.so.0.0.0
	libpcsclite.so.1 -> libpcsclite.so.1.0.0
	libabrt_web.so.0 -> libabrt_web.so.0.0.1
	libustr-1.0.so.1 -> libustr-1.0.so.1.0.4
	libgvfscommon-dnssd.so.0 -> libgvfscommon-dnssd.so.0.0.0
	libpulse.so.0 -> libpulse.so.0.12.2
	libtiffxx.so.3 -> libtiffxx.so.3.9.4
	libelf.so.1 -> libelf-0.161.so
	libnm-glib.so.2 -> libnm-glib.so.2.7.0
	libpng.so.3 -> libpng.so.3.49.0
	libopcodes-2.20.51.0.2-5.43.el6.so -> libopcodes-2.20.51.0.2-5.43.el6.so
	libI810XvMC.so.1 -> libI810XvMC.so.1.0.0
	libck-connector.so.0 -> libck-connector.so.0.0.0
	libusbpp-0.1.so.4 -> libusbpp-0.1.so.4.4.4
	libcups.so.2 -> libcups.so.2
	libXaw.so.7 -> libXaw7.so.7.0.0
	libXcursor.so.1 -> libXcursor.so.1.0.2
	libQtHelp.so.4 -> libQtHelp.so.4.6.2
	libLLVM-3.4-mesa.so -> libLLVM-3.4-mesa.so
	libQtSql.so.4 -> libQtSql.so.4.6.2
	libXft.so.2 -> libXft.so.2.3.1
	libcupsdriver.so.1 -> libcupsdriver.so.1
	libgdmsimplegreeter.so.1 -> libgdmsimplegreeter.so.1.0.0
	libXmu.so.6 -> libXmu.so.6.2.0
	libeststring.so.1.2 -> libeststring.so.1.2
	libpth.so.20 -> libpth.so.20.0.27
	libXvMC.so.1 -> libXvMC.so.1.0.0
	libebackend-1.2.so.0 -> libebackend-1.2.so.0.0.1
	libkdb5.so.6 -> libkdb5.so.6.0
	libcupscgi.so.1 -> libcupscgi.so.1
	libpyglib-2.0-python.so.0 -> libpyglib-2.0-python.so.0.0.0
	libthai.so.0 -> libthai.so.0.1.4
	libavc1394.so.0 -> libavc1394.so.0.3.0
	libvte.so.9 -> libvte.so.9.2501.0
	librpmio.so.1 -> librpmio.so.1.0.0
	libgif.so.4 -> libgif.so.4.1.6
	libunique-1.0.so.0 -> libunique-1.0.so.0.0.0
	libxcb-screensaver.so.0 -> libxcb-screensaver.so.0.0.0
	libusb-1.0.so.0 -> libusb-1.0.so.0.1.0
	libgnome-mag.so.2 -> libgnome-mag.so.2.3.9
	libevent_extra-1.4.so.2 -> libevent_extra-1.4.so.2.1.3
	libcamel-provider-1.2.so.19 -> libcamel-provider-1.2.so.19.0.0
	libuser.so.1 -> libuser.so.1.2.2
	libxcb-damage.so.0 -> libxcb-damage.so.0.0.0
	libgnutls-extra.so.26 -> libgnutls-extra.so.26.14.12
	libraw1394.so.11 -> libraw1394.so.11.0.1
	libxcb-reply.so.1 -> libxcb-reply.so.1.0.0
	libtheoraenc.so.1 -> libtheoraenc.so.1.1.2
	libsmime3.so -> libsmime3.so
	libdaemon.so.0 -> libdaemon.so.0.5.0
	libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.2400.23
	libdrm_radeon.so.1 -> libdrm_radeon.so.1.0.1
	libXfont.so.1 -> libXfont.so.1.4.1
	libcanberra.so.0 -> libcanberra.so.0.2.1
	libXdamage.so.1 -> libXdamage.so.1.1.0
	libcairo.so.2 -> libcairo.so.2.10800.8
	libbonoboui-2.so.0 -> libbonoboui-2.so.0.0.0
	librpm.so.1 -> librpm.so.1.0.0
	libcdio_paranoia.so.0 -> libcdio_paranoia.so.0.0.3
	libssl.so.10 -> libssl.so.1.0.1e
	libXpm.so.4 -> libXpm.so.4.11.0
	libasm.so.1 -> libasm-0.161.so
	libspi.so.0 -> libspi.so.0.10.11
	libEGL.so.1 -> libEGL.so.1.0.0
	libsndfile.so.1 -> libsndfile.so.1.0.20
	libxcb-xinerama.so.0 -> libxcb-xinerama.so.0.0.0
	libiec61883.so.0 -> libiec61883.so.0.1.1
	libhunspell-1.2.so.0 -> libhunspell-1.2.so.0.0.0
	libnm-glib-vpn.so.1 -> libnm-glib-vpn.so.1.1.0
	libQt3Support.so.4 -> libQt3Support.so.4.6.2
	libXrandr.so.2 -> libXrandr.so.2.2.0
	libgs.so.8 -> libgs.so.8.70
	libgnutls.so.26 -> libgnutls.so.26.14.12
	libhistory.so.6 -> libhistory.so.6.0
	libedata-cal-1.2.so.10 -> libedata-cal-1.2.so.10.0.0
	libform.so.5 -> libform.so.5.7
	libply-splash-graphics.so.2 -> libply-splash-graphics.so.2.0.0
	libxcb-xevie.so.0 -> libxcb-xevie.so.0.0.0
	libX11-xcb.so.1 -> libX11-xcb.so.1.0.0
	libexif.so.12 -> libexif.so.12.3.3
	libjasper.so.1 -> libjasper.so.1.0.0
	libxcb-xselinux.so.0 -> libxcb-xselinux.so.0.0.0
	libcanberra-gtk.so.0 -> libcanberra-gtk.so.0.1.5
	libformw.so.5 -> libformw.so.5.7
	libfontconfig.so.1 -> libfontconfig.so.1.4.4
	libgnomecanvas-2.so.0 -> libgnomecanvas-2.so.0.2600.0
	libQtDesignerComponents.so.4 -> libQtDesignerComponents.so.4.6.2
	libgtop-2.0.so.7 -> libgtop-2.0.so.7.2.0
	libcloog.so.0 -> libcloog.so.0.0.0
	libxslt.so.1 -> libxslt.so.1.1.26
	libdrm.so.2 -> libdrm.so.2.4.0
	libgettextlib-0.17.so -> libgettextlib-0.17.so
	libbonobo-2.so.0 -> libbonobo-2.so.0.0.0
	libexslt.so.0 -> libexslt.so.0.8.15
	libcspi.so.0 -> libcspi.so.0.10.11
	libcdda_interface.so.0 -> libcdda_interface.so.0.10.2
	libnotify.so.1 -> libnotify.so.1.2.3
	libmp.so.3 -> libmp.so.3.1.14
	libORBitCosNaming-2.so.0 -> libORBitCosNaming-2.so.0.1.0
	libppl.so.7 -> libppl.so.7.1.0
	libnautilus-extension.so.1 -> libnautilus-extension.so.1.1.0
	libXxf86vm.so.1 -> libXxf86vm.so.1.0.0
	libxmlrpc_server.so.3 -> libxmlrpc_server.so.3.16
	libxmlrpc_server_abyss.so.3 -> libxmlrpc_server_abyss.so.3.16
	libdb_cxx-4.7.so -> libdb_cxx.so
	libsnappy.so.1 -> libsnappy.so.1.1.4
	libgettextsrc-0.17.so -> libgettextsrc-0.17.so
	libpangox-1.0.so.0 -> libpangox-1.0.so.0.2800.1
	libabrt_dbus.so.0 -> libabrt_dbus.so.0.0.1
	libgstcdda-0.10.so.0 -> libgstcdda-0.10.so.0.20.0
	libxcb-dpms.so.0 -> libxcb-dpms.so.0.0.0
	libxcb-record.so.0 -> libxcb-record.so.0.0.0
	libQtOpenGL.so.4 -> libQtOpenGL.so.4.6.2
	libpng12.so.0 -> libpng12.so.0.49.0
	libcurl.so.4 -> libcurl.so.4.1.1
	libxklavier.so.15 -> libxklavier.so.15.0.0
	librsvg-2.so.2 -> librsvg-2.so.2.26.0
	libsmbclient.so.0 -> libsmbclient.so.0
	libgdu.so.0 -> libgdu.so.0.0.0
	libudf.so.0 -> libudf.so.0.0.0
	libfontenc.so.1 -> libfontenc.so.1.0.0
	libgucharmap.so.7 -> libgucharmap.so.7.0.0
	libstartup-notification-1.so.0 -> libstartup-notification-1.so.0.0.0
	libnetapi.so.0 -> libnetapi.so.0
	libgnome-menu.so.2 -> libgnome-menu.so.2.4.1
	libproxy.so.0 -> libproxy.so.0.0.0
	libxmlrpc_server_cgi.so.3 -> libxmlrpc_server_cgi.so.3.16
	libxcb-res.so.0 -> libxcb-res.so.0.0.0
	libpangocairo-1.0.so.0 -> libpangocairo-1.0.so.0.2800.1
	libutempter.so.0 -> libutempter.so.1.1.5
	libgstrtsp-0.10.so.0 -> libgstrtsp-0.10.so.0.20.0
	libsgutils2.so.2 -> libsgutils2.so.2.0.0
	libxcb-render.so.0 -> libxcb-render.so.0.0.0
	libdb-4.7.so -> libdb.so
	libxcb-property.so.1 -> libxcb-property.so.1.0.0
	libxml2.so.2 -> libxml2.so.2.7.6
	libQtTest.so.4 -> libQtTest.so.4.6.2
	libgbm.so.1 -> libgbm.so.1.0.0
	libmpfr.so.1 -> libmpfr.so.1.2.0
	libgsf-1.so.114 -> libgsf-1.so.114.0.15
	libverto.so.0 -> libverto.so.0.0
	libXfixes.so.3 -> libXfixes.so.3.1.0
	libxcb-xf86dri.so.0 -> libxcb-xf86dri.so.0.0.0
	libQtCLucene.so.4 -> libQtCLucene.so.4.6.2
	libkadm5clnt_mit.so.8 -> libkadm5clnt_mit.so.8.0
	libdmx.so.1 -> libdmx.so.1.0.0
	libdrm_nouveau.so.1 -> libdrm_nouveau.so.1.0.0
	libpcrecpp.so.0 -> libpcrecpp.so.0.0.0
	libcroco-0.6.so.3 -> libcroco-0.6.so.3.0.1
	libxcb-event.so.1 -> libxcb-event.so.1.0.0
	libpanelw.so.5 -> libpanelw.so.5.7
	libpackagekit-glib.so.12 -> libpackagekit-glib.so.12.0.6
	libecal-1.2.so.8 -> libecal-1.2.so.8.2.2
	libQtSvg.so.4 -> libQtSvg.so.4.6.2
	libxcb-xfixes.so.0 -> libxcb-xfixes.so.0.0.0
	libQtScript.so.4 -> libQtScript.so.4.6.2
	libvorbisenc.so.2 -> libvorbisenc.so.2.0.6
	libxmlrpc_client.so.3 -> libxmlrpc_client.so.3.16
	libnsspem.so -> libnsspem.so
	libxcb-xv.so.0 -> libxcb-xv.so.0.0.0
	libppl_c.so.2 -> libppl_c.so.2.1.0
	libv4l2.so.0 -> libv4l2.so.0
	libverto-k5ev.so.0 -> libverto-k5ev.so.0.0
	libgstreamer-0.10.so.0 -> libgstreamer-0.10.so.0.25.0
	libtalloc.so.2 -> libtalloc.so.2.1.5
	libasyncns.so.0 -> libasyncns.so.0.3.1
	libgdk-x11-2.0.so.0 -> libgdk-x11-2.0.so.0.2400.23
	libgstfft-0.10.so.0 -> libgstfft-0.10.so.0.20.0
	libwacom.so.2 -> libwacom.so.2.1.0
	libpanel-applet-2.so.0 -> libpanel-applet-2.so.0.2.68
	libIntelXvMC.so.1 -> libIntelXvMC.so.1.0.0
	libXv.so.1 -> libXv.so.1.0.0
	libedataserver-1.2.so.14 -> libedataserver-1.2.so.14.0.0
	libgp11.so.0 -> libgp11.so.0.0.0
	libvorbis.so.0 -> libvorbis.so.0.4.3
	libapr-1.so.0 -> libapr-1.so.0.3.9
	libQtXml.so.4 -> libQtXml.so.4.6.2
	libicalvcal.so.0 -> libicalvcal.so.0.43.0
	libgstsdp-0.10.so.0 -> libgstsdp-0.10.so.0.20.0
	libwavpack.so.1 -> libwavpack.so.1.1.3
	libtag_c.so.0 -> libtag_c.so.0.0.0
	libXtst.so.6 -> libXtst.so.6.1.0
	libgpgme.so.11 -> libgpgme.so.11.6.6
	libFLAC++.so.6 -> libFLAC++.so.6.2.0
	libgstaudio-0.10.so.0 -> libgstaudio-0.10.so.0.20.0
	libcdio++.so.0 -> libcdio++.so.0.0.0
	libcrypto.so.10 -> libcrypto.so.1.0.1e
	libreport.so.0 -> libreport.so.0.0.1
	libmng.so.1 -> libmng.so.1.0.0
	libxmlrpc.so.3 -> libxmlrpc.so.3.16
	libxcb-atom.so.1 -> libxcb-atom.so.1.0.0
	libgnome-keyring.so.0 -> libgnome-keyring.so.0.1.1
	libgnomespeech.so.7 -> libgnomespeech.so.7.0.1
	libp11-kit.so.0 -> libp11-kit.so.0.0.0
	libavahi-common.so.3 -> libavahi-common.so.3.5.1
	libstdc++.so.5 -> libstdc++.so.5.0.7
	libFestival.so.1.96.0 -> libFestival.so.1.96.0
	libusb-0.1.so.4 -> libusb-0.1.so.4.4.4
	libxcb-render-util.so.0 -> libxcb-render-util.so.0.0.0
	libsmbsharemodes.so.0 -> libsmbsharemodes.so.0
	libjpeg.so.62 -> libjpeg.so.62.0.0
	libaprutil-1.so.0 -> libaprutil-1.so.0.3.9
	libavahi-client.so.3 -> libavahi-client.so.3.2.5
	libxcb-sync.so.0 -> libxcb-sync.so.0.0.0
	libgnome-desktop-2.so.11 -> libgnome-desktop-2.so.11.4.2
	libnm-util.so.1 -> libnm-util.so.1.9.0
	libgdata.so.7 -> libgdata.so.7.2.0
	libfreetype.so.6 -> libfreetype.so.6.3.22
	libgnome-2.so.0 -> libgnome-2.so.0.2800.0
	libxcb-dri2.so.0 -> libxcb-dri2.so.0.0.0
	libxcb-shm.so.0 -> libxcb-shm.so.0.0.0
	libgnomekbd.so.4 -> libgnomekbd.so.4.0.0
	libsatyr.so.3 -> libsatyr.so.3.0.0
	libart_lgpl_2.so.2 -> libart_lgpl_2.so.2.3.20
	libogg.so.0 -> libogg.so.0.6.0
	libssh2.so.1 -> libssh2.so.1.0.1
	libgconf-2.so.4 -> libgconf-2.so.4.1.5
	libgnome-window-settings.so.1 -> libgnome-window-settings.so.1.0.0
	libgweather.so.1 -> libgweather.so.1.5.2
	libGL.so.1 -> libGL.so.1.2.0
	libltdl.so.7 -> libltdl.so.7.2.1
	libexempi.so.3 -> libexempi.so.3.2.0
	libstdc++.so.6 -> libstdc++.so.6.0.13
	libpcprofile.so -> libpcprofile.so
	libgnomekbdui.so.4 -> libgnomekbdui.so.4.0.0
	libatasmart.so.4 -> libatasmart.so.4.0.3
	libmtdev.so.1 -> libmtdev.so.1.0.0
	libxcb-xvmc.so.0 -> libxcb-xvmc.so.0.0.0
	libcdda_paranoia.so.0 -> libcdda_paranoia.so.0.10.2
	libQtDesigner.so.4 -> libQtDesigner.so.4.6.2
	libgnome-media-profiles.so.0 -> libgnome-media-profiles.so.0.0.0
	libglade-2.0.so.0 -> libglade-2.0.so.0.0.7
	libxmlrpc_abyss.so.3 -> libxmlrpc_abyss.so.3.16
	libQtGui.so.4 -> libQtGui.so.4.6.2
	libreport-gtk.so.0 -> libreport-gtk.so.0.0.1
	libffi.so.5 -> libffi.so.5.0.6
	libXvMCW.so.1 -> libXvMCW.so.1.0.0
	libgstinterfaces-0.10.so.0 -> libgstinterfaces-0.10.so.0.20.0
	libegroupwise-1.2.so.13 -> libegroupwise-1.2.so.13.0.1
	libpcreposix.so.0 -> libpcreposix.so.0.0.0
	libgnomevfs-2.so.0 -> libgnomevfs-2.so.0.2400.2
	libiso9660++.so.0 -> libiso9660++.so.0.0.0
	libslang.so.2 -> libslang.so.2.2.1
	libgcr.so.0 -> libgcr.so.0.0.0
	libcdio.so.10 -> libcdio.so.10.0.0
	libtdb.so.1 -> libtdb.so.1.3.8
	libarchive.so.2 -> libarchive.so.2.8.3
	libgsttag-0.10.so.0 -> libgsttag-0.10.so.0.20.0
	libXss.so.1 -> libXss.so.1.0.0
	libpackagekit-glib2.so.12 -> libpackagekit-glib2.so.12.0.6
	libICE.so.6 -> libICE.so.6.3.0
	libSM.so.6 -> libSM.so.6.0.1
	libQtDBus.so.4 -> libQtDBus.so.4.6.2
	libpcap.so.1 -> libpcap.so.1.4.0
	libgvfscommon.so.0 -> libgvfscommon.so.0.0.0
	libpulse-simple.so.0 -> libpulse-simple.so.0.0.3
	libQtMultimedia.so.4 -> libQtMultimedia.so.4.6.2
	libXxf86dga.so.1 -> libXxf86dga.so.1.0.0
	libical.so.0 -> libical.so.0.43.0
	librarian.so.0 -> librarian.so.0.0.0
	libglamor.so.0 -> libglamor.so.0.0.0
	libsamplerate.so.0 -> libsamplerate.so.0.1.7
	libgudev-1.0.so.0 -> libgudev-1.0.so.0.0.1
	libv4l1.so.0 -> libv4l1.so.0
	libmemusage.so -> libmemusage.so
	libwnck-1.so.22 -> libwnck-1.so.22.3.23
	libevent_core-1.4.so.2 -> libevent_core-1.4.so.2.1.3
	libpolkit-gobject-1.so.0 -> libpolkit-gobject-1.so.0.0.0
	libedit.so.0 -> libedit.so.0.0.27
	libgdk_pixbuf-2.0.so.0 -> libgdk_pixbuf-2.0.so.0.2400.1
	libchromeXvMC.so.1 -> libchromeXvMC.so.1.0.0
	libgailutil.so.18 -> libgailutil.so.18.0.1
	libQtScriptTools.so.4 -> libQtScriptTools.so.4.6.2
	libedataserverui-1.2.so.11 -> libedataserverui-1.2.so.11.0.0
	libxcb.so.1 -> libxcb.so.1.1.0
	libgstpbutils-0.10.so.0 -> libgstpbutils-0.10.so.0.20.0
	libgstbase-0.10.so.0 -> libgstbase-0.10.so.0.25.0
	libdw.so.1 -> libdw-0.161.so
	libxcb-aux.so.0 -> libxcb-aux.so.0.0.0
	libatk-1.0.so.0 -> libatk-1.0.so.0.3009.1
	libgdbm.so.2 -> libgdbm.so.2.0.0
	libdv.so.4 -> libdv.so.4.0.3
	libxkbfile.so.1 -> libxkbfile.so.1.0.2
	libXt.so.6 -> libXt.so.6.0.0
	libfa.so.1 -> libfa.so.1.4.0
	libmcpp.so.0 -> libmcpp.so.0.3.0
	liblz4.so.1 -> liblz4.so.1.7.1
	libXrender.so.1 -> libXrender.so.1.3.0
	libXau.so.6 -> libXau.so.6.0.0
	libicalss.so.0 -> libicalss.so.0.43.0
	libpulsecore-0.9.21.so -> libpulsecore-0.9.21.so
	libQtXmlPatterns.so.4 -> libQtXmlPatterns.so.4.6.2
	libXinerama.so.1 -> libXinerama.so.1.0.0
	libmetacity-private.so.0 -> libmetacity-private.so.0.0.0
	libphonon.so.4 -> libphonon.so.4.3.1
	libXmuu.so.1 -> libXmuu.so.1.0.0
	libsqlite3.so.0 -> libsqlite3.so.0.8.6
	libeggdbus-1.so.0 -> libeggdbus-1.so.0.0.0
	libloginhelper.so.0 -> libloginhelper.so.0.0.0
	libvisual-0.4.so.0 -> libvisual-0.4.so.0.0.0
	libtic.so.5 -> libtic.so.5.7
	libkadm5srv_mit.so.8 -> libkadm5srv_mit.so.8.0
	libnewt.so.0.52 -> libnewt.so.0.52.11
	libvorbisfile.so.3 -> libvorbisfile.so.3.3.2
	libbonobo-activation.so.4 -> libbonobo-activation.so.4.0.0
	libv4lconvert.so.0 -> libv4lconvert.so.0
	libQtCore.so.4 -> libQtCore.so.4.6.2
	libxcb-randr.so.0 -> libxcb-randr.so.0.1.0
/lib/i686: (hwcap: 0x0008000000000000)
/lib64/tls: (hwcap: 0x8000000000000000)
/usr/lib64/tls: (hwcap: 0x8000000000000000)
/usr/lib64/sse2: (hwcap: 0x0000000004000000)
/lib/i686/nosegneg: (hwcap: 0x0028000000000000)
	libpthread.so.0 -> libpthread-2.12.so
	libm.so.6 -> libm-2.12.so
	librt.so.1 -> librt-2.12.so
	libthread_db.so.1 -> libthread_db-1.0.so
	libc.so.6 -> libc-2.12.so
*/
```

##### Check the current value of LD_LIBRARY_PATH
```
echo $LD_LIBRARY_PATH
```

##### Set the environment variable LD_LIBRARY_PATH to the appropriate directory for the Instant Client version
```
export LD_LIBRARY_PATH=/usr/lib/oracle/12.2/client64/lib:$LD_LIBRARY_PATH
```

##### Check the current value of LD_LIBRARY_PATH
```
echo $LD_LIBRARY_PATH
```

##### Open sqlplus
```
sqlplus64
```
