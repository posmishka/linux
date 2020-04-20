snippets
========

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

mysqlcheck -u user -p --optimize database_name

repair table <table_name>;

 describe tablename;
