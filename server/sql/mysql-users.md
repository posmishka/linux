mysql-users
===========

## restoring root (if deleted)

```
Add 'skip-grant-tables' to my.cnf under the [mysqld] section
restart mysql
type mysql with no password and hit enter
Run This:
DELETE FROM mysql.user 
WHERE  user = 'root' 
       AND host = 'localhost'; 
```
