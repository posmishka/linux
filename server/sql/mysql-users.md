mysql-users
===========

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
**Create user root (variant 2)**
```
INSERT INTO mysql.user SET
                  Host = 'localhost',
                  User = 'root',
              Password = PASSWORD('VhcUI12gpVs'),
           Select_priv = 'Y',
           Insert_priv = 'Y',
           Update_priv = 'Y',
           Delete_priv = 'Y',
           Create_priv = 'Y',
             Drop_priv = 'Y',
           Reload_priv = 'Y',
         Shutdown_priv = 'Y',
          Process_priv = 'Y',
             File_priv = 'Y',
            Grant_priv = 'Y',
       References_priv = 'Y',
            Index_priv = 'Y',
            Alter_priv = 'Y',
          Show_db_priv = 'Y',
            Super_priv = 'Y',
 Create_tmp_table_priv = 'Y',
      Lock_tables_priv = 'Y',
          Execute_priv = 'Y',
       Repl_slave_priv = 'Y',
      Repl_client_priv = 'Y',
      Create_view_priv = 'Y',
        Show_view_priv = 'Y',
   Create_routine_priv = 'Y',
    Alter_routine_priv = 'Y',
      Create_user_priv = 'Y',
            Event_priv = 'Y',
          Trigger_priv = 'Y',
Create_tablespace_priv = 'Y',
              ssl_type = '',
              ssl_cipher = '',
             x509_issuer = '',
            x509_subject = '',
           max_questions = 0,
             max_updates = 0,
         max_connections = 1000000,
    max_user_connections = 1000000,
   authentication_string = '',
;