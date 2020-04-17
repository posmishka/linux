mysql
=====

 г) скрипт для создания пользователей mysql
 tee /home/sasha_fox/create_db.sh <<-'EOF'
 NAME=[ИМЯ БАЗЫ, ПОЛЬЗОВАТЕЛЯ]
 PASS=[ПАРОЛЬ БАЗЫ]
 mysql -u root -p -e 'CREATE DATABASE $NAME;'
 mysql -u root -p -e 'grant all privileges on $NAME.* to $NAME@localhost identified by "$PASS";'
 mysql -u root -p -e 'flush privileges;'
 EOF

 sh /home/sasha_fox/create_db.sh [ИМЯ_БАЗЫ/ПОЛЬЗОВАТЕЛЯ] [ПАРОЛЬ]
 