config
======
```
[www-traverse]

listen = /var/run/php-fpm/traverse.sock
;listen.backlog = -1
;listen.allowed_clients = 127.0.0.1

listen.owner = nginx 
listen.group = nginx
listen.mode = 0666

user = traverse
group = traverse

pm = ondemand

pm.max_children = 10
pm.start_servers = 3
pm.process_idle_timeout = 30s
pm.min_spare_servers = 3
pm.max_spare_servers = 10
pm.max_requests = 0

pm.status_path = /status1111

;pm.status_path = /status
;ping.path = /ping

;request_terminate_timeout = 0
request_slowlog_timeout = 30s
slowlog = /home/traverse/logs/slow.log
 
;rlimit_files = 1024
;rlimit_core = 0
 
;chroot = /home/www/
;chdir = /
 
;catch_workers_output = yes
 
;security.limit_extensions = .php .php3 .php4 .php5

;env[HOSTNAME] = $HOSTNAME
env[PATH] = /usr/local/bin:/usr/bin:/bin
;env[TMP] = /tmp
;env[TMPDIR] = /tmp
;env[TEMP] = /tmp

php_admin_value[sendmail_path] = /usr/sbin/sendmail -t -i -f no-reply@server.com
php_flag[display_errors] = on
php_admin_value[error_log] = /var/log/php-fpm/$pool-error.log
php_admin_flag[log_errors] = on
php_admin_value[memory_limit] = 128M

; Set session path to a directory owned by process user
php_value[session.save_handler] = files
php_value[session.save_path]    = /var/lib/php/session-traverse
php_value[soap.wsdl_cache_dir]  = /var/lib/php/wsdlcache-traverse

;php_value[error_reporting] = 22519
;php_value[open_basedir] = "/var/www/vhosts/server.artkamin.ua/:/tmp/:/usr/share/phpMyAdmin/:/usr/share/pear:/usr/share/php:/etc/phpMyAdmin/:doc/html/"
```
```
[insecret_co]
user = insecret
group = insecret

listen = /var/run/php-fpm/73-insecret_co.sock
listen.backlog = 2048

listen.owner = nginx
listen.group = nginx
listen.mode = 0660

pm = dynamic 
pm.max_children = 100
pm.start_servers = 50
pm.min_spare_servers = 20
pm.max_spare_servers = 50
pm.max_requests = 20000
;pm.status_path = /phpfpm-status

slowlog = /var/log/php-fpm/$pool-slow.log
request_slowlog_timeout = 300s

request_terminate_timeout = 360s

catch_workers_output = no

php_admin_value[error_log] = /var/log/php-fpm/$pool-error.log
php_admin_flag[log_errors] = on

php_value[session.save_handler] = files
php_value[session.save_path]    = /var/lib/php/session/insecret_co
php_value[soap.wsdl_cache_dir]  = /var/lib/php/wsdlcache/insecret_co
```