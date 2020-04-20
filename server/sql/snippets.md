snippets
========
**import database**

    $ mysql -u USER -p DATABASE < db_name.sql

**import from archive**

    gunzip < db_name.sql.gz | mysql -u USER -pPASSWORD DATABASE

**export database**

    $ mysqldump -u USER -p DATABASE > db_name.sql

**export all databases**

    $ mysqldump -uroot -p -A > alldb.sql
    
**export and archieve**

    mysqldump -u USER -pPASSWORD DATABASE | gzip > db_name.sql.gz


mysqldump -u[USERNAME] -p[PASSWORD] --add-drop-table --no-data [DATABASE] | grep ^DROP | mysql -u[USERNAME] -p[PASSWORD] [DATABASE]

**show variable**  
`SHOW GLOBAL VARIABLES WHERE variable_name = 'max_allowed_packet';`

**set variable**  
`set global max_allowed_packet = 20971520`


### find mysql config
```
$ which mysqld
/usr/sbin/mysqld
$ /usr/sbin/mysqld --verbose --help | grep -A 1 "Default options"
```

**optimize database**  
`mysqlcheck -u user -p --optimize database_name`
