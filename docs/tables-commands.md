# show all tables

## References
* http://onewebsql.com/blog/list-all-tables

##### Connect to the database
```
sqlplus username/password@database-name
```

##### List all tables owned by the current user
```sql
select tablespace_name, table_name from user_tables;
```

##### List all tables in a database
```sql
select tablespace_name, table_name from dba_tables;
```

##### List all tables accessible to the current user
```sql
select tablespace_name, table_name from all_tables;
```

##### Describe a table
```sql
desc <table_name>
```
