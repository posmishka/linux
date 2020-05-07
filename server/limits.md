limits
======
### проверить открытые файлы
cat /proc/$(cat /var/run/mariadb/mariadb.pid)/limits | grep open.files

### от пользователя
su - mysql -c 'ulimit -a' -s '/bin/bash' | grep open