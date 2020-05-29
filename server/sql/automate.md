automate
=====

##
 tee create_db.sh <<-'EOF'
 NAME=[ИМЯ БАЗЫ, ПОЛЬЗОВАТЕЛЯ]
 PASS=[ПАРОЛЬ БАЗЫ]
 mysql -u root -p -e 'CREATE DATABASE ${NAME};'
 mysql -u root -p -e 'grant all privileges on ${NAME}.* to ${NAME}@localhost identified by "${PASS}";'
 mysql -u root -p -e 'flush privileges;'
 EOF