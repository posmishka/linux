limits
======
### проверить открытые файлы
cat /proc/$(cat /var/run/mariadb/mariadb.pid)/limits | grep open.files

