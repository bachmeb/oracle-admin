# USER_ROLE_PRIVS

## References
* http://stackoverflow.com/questions/15066408/how-to-find-the-privileges-and-roles-granted-to-a-user-in-oracle
* http://docs.oracle.com/cd/B10501_01/server.920/a96521/privs.htm#15665
 
##### USER view lists roles granted to the current user.
```sql
select * from USER_ROLE_PRIVS;
```
```
USERNAME GRANTED_ROLE ADMIN_OPTION DEFAULT_ROLE OS_GRANTED
```
