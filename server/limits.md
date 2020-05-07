limits
======
### проверить о
cat /proc/$(cat /var/run/mariadb/mariadb.pid)/limits | grep open.files