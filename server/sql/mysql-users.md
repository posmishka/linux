mysql-users
===========

## change root password
1. stop mysql service

    `service mysql stop && ps awx | grep mysqld`

2. start mysql in safe mode

    mysqld_safe --skip-grant-tables
    
 3

## restoring root (if corrupted)

**Delete user**
```
1. Add 'skip-grant-tables' to my.cnf under the [mysqld] section
2. restart mysql
3. type mysql with no password and hit enter
4. DELETE FROM mysql.user WHERE  user = 'root' AND host = 'localhost'; 
```
**Create user root (variant 1)**
```
INSERT INTO mysql.user 
SET user = 'root', 
    host = 'localhost', 
    password = Password('VhcUI12gpVs'), 
    Select_priv = 'y',
    Insert_priv = 'y',
    Update_priv = 'y',
    Delete_priv = 'y',
    Create_priv = 'y',
    Drop_priv = 'y',
    Reload_priv = 'y',
    Shutdown_priv = 'y',
    Process_priv = 'y',
    File_priv = 'y',
    Grant_priv = 'y',
    References_priv = 'y',
    Index_priv = 'y',
    Alter_priv = 'y',
    Show_db_priv = 'y',
    Super_priv = 'y',
    Create_tmp_table_priv = 'y',
    Lock_tables_priv = 'y',
    Execute_priv = 'y',
    Repl_slave_priv = 'y',
    Repl_client_priv = 'y',
    Create_view_priv = 'y',
    Show_view_priv = 'y',
    Create_routine_priv = 'y',
    Alter_routine_priv = 'y',
    Create_user_priv = 'y',
    Event_priv = 'y',
    Trigger_priv = 'y',
    Create_tablespace_priv = 'y';
exit from mysql
remove 'skip-grant-tables' from my.cnf under the [mysqld] section
restart mysql
```
