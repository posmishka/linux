limits
======
### проверить открытые файлы
    cat /proc/$(cat /var/run/mariadb/mariadb.pid)/limits | grep open.files

### от пользователя
    su - mysql -c 'ulimit -a' -s '/bin/bash' | grep open

### сервис
    /usr/lib/systemd/system/mariadb.service
    LimitNOFILE=infinity
    LimitMEMLOCK=infinity

infinity = 65535

    systemctl daemon-reload
    systemctl restart mariadb
 
 ### sysctl
     vi /etc/sysctl.conf
     sysctl -p
 
 ### limits.conf
 
/etc/security/limits.conf

    mysql           soft    nofile          65535
    mysql           hard    nofile          65535

reboot