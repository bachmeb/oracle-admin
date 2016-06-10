# TO_CHAR()

## References
* http://docs.oracle.com/cd/B19306_01/server.102/b14200/functions180.htm

##### Convert date value to new format
```
TO_CHAR( someDate, 'YYYY-MON-DD' ) as theDate,
```
```
TO_CHAR(ts_col, 'DD-MON-YYYY HH24:MI:SSxFF')
```
```
TO_CHAR(tstz_col, 'DD-MON-YYYY HH24:MI:SSxFF TZH:TZM')
```
