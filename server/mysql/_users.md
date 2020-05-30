_users
=====
### MYSQL 8

CREATE USER 'yourUserName'@'localhost' IDENTIFIED BY 'yourPassword';
GRANT ALL ON *.* TO 'yourUserName'@'localhost';
flush privileges;



### create user sh
```
 tee create_db.sh <<-'EOF'
 NAME=[ИМЯ БАЗЫ, ПОЛЬЗОВАТЕЛЯ]
 PASS=[ПАРОЛЬ БАЗЫ]
 mysql -u root -p -e 'CREATE DATABASE ${NAME};'
 mysql -u root -p -e 'grant all privileges on ${NAME}.* to ${NAME}@localhost identified by "${PASS}";'
 mysql -u root -p -e 'flush privileges;'
 EOF
 ```