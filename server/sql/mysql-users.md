mysql-users
===========

## restoring root (if corrupted)

Delete user
```
1. Add 'skip-grant-tables' to my.cnf under the [mysqld] section
2. restart mysql
3. type mysql with no password and hit enter
4. DELETE FROM mysql.user WHERE  user = 'root' AND host = 'localhost'; 
```
Create user root
