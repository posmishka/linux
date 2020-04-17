LEMP Install
========================
# Nginx

*we will build the most recent version from source with custom modules to have http/2 enabled*  

* [] Install Dev Tools we need  

*we will need to remove them adter the building process*

	yum -y groupinstall 'Development Tools'
	yum -y install wget openssl-devel libxml2-devel libxslt-devel gd-devel perl-ExtUtils-Embed GeoIP-devel

 * [] Setting variables  

*we will use openssl 1.0.2 branch from www.openssl.org/source/* 

	OPENSSL="openssl-1.0.2k"

*nginx is the last stable from https://nginx.org/en/download.html* 
	
	NGINX="nginx-1.16.1"

* [] Installing basic nginx

>> PLACEHOLDER 
  
* [] Installing PHP7

*we will use custom repo for php* 

	rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
	yum update
	yum install -y php70w php70w-opcache php70w-fpm php70w-gd php70w-mcrypt php70w-mysqlnd php70w-odbc php70w-pdo php70w-pecl-apcu php70w-xml php70w-mbstring  php70w-soap  
	 
  
 systemctl enable php-fpm && systemctl start php-fpm

 chown -R nginx:nginx /var/lib/php/session /var/lib/php/wsdlcache /home/www /var/cache/nginx/pagespeed

  * [] MariaDB Install

*creating a repo*

	 tee /etc/yum.repos.d/Mariadb.repo <<-'EOF' 
	 # http://mariadb.org/mariadb/repositories/
	 [mariadb]  
	 name = MariaDB  
	 baseurl = http://yum.mariadb.org/10.1/centos7-amd64  
	 gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB  
	 gpgcheck=1  
	 EOF
	 
*installing mariadb along with phpmyadmin and mysqltuner*

	yum -y install mariadb-server mariadb phpmyadmin mysqltuner && \
	systemctl start mariadb &&
	systemctl enable mariadb
 
  
 в) создать пароль mysql рут, Y на все вопросы дальше
 mysql_secure_installation  
 
  
 г) скрипт для создания пользователей mysql
 tee /home/sasha_fox/create_db.sh <<-'EOF'
 NAME=[ИМЯ БАЗЫ, ПОЛЬЗОВАТЕЛЯ]
 PASS=[ПАРОЛЬ БАЗЫ]
 mysql -u root -p -e 'CREATE DATABASE $NAME;'
 mysql -u root -p -e 'grant all privileges on $NAME.* to $NAME@localhost identified by "$PASS";'
 mysql -u root -p -e 'flush privileges;'
 EOF

 sh /home/sasha_fox/create_db.sh [ИМЯ_БАЗЫ/ПОЛЬЗОВАТЕЛЯ] [ПАРОЛЬ]
 
  
 д) проверить настройки phpmyadmin, должен открываться по адресу /pma3388/
 посмотреть настройки : vim /etc/nginx/conf.d/phpmyadmin.cfg
  mkdir /home/www
 все файлы сайта должны быть в /home/www/site.com
   
 

 yum install -y phpmyadmin
 mkdir /home/www/site.com/pma54321
 
  
 ln -s /usr/share/phpMyAdmin/ /home/www/site.com/pma54321
 
  
 location /pma54321/ {
         alias /usr/share/phpMyAdmin/;
         location ~ \.php$ {
                 fastcgi_pass unix:/var/run/php5-fpm.sock;
                 fastcgi_index index.php;
                 include fastcgi_params;
                 fastcgi_param SCRIPT_FILENAME $request_filename;
                 fastcgi_ignore_client_abort off;
                 }
 }    
 10) разное
 запускать только в папке сайта - устанавливает права 755 на категории, 644 на файлы
 find ./ -type d|xargs chmod 755 && find ./ -type f |xargs chmod 644  
 