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

 в) установка nginx с версией openssl 1.0.2j для поддержки http2
 mkdir -p /root/openssl && \
 wget https://www.openssl.org/source/$OPENSSL.tar.gz -O /root/openssl/$OPENSSL.tar.gz && \
 tar -zxvf /root/openssl/$OPENSSL.tar.gz -C /root/openssl
    
  
 
  
 г) опционально - установка модуля pagespeed google
 NGINX="nginx-1.11.13" && wget http://nginx.org/download/$NGINX.tar.gz ; tar xvzf $NGINX.tar.gz ; rm -rf $NGINX.tar.gz ; cd $NGINX
 bash <(curl -f -L -sS https://ngxpagespeed.com/install) -v 1.11.33.4
 
  
 nginx -V
 скопировать строчку после configure arguments:
  
 cd /root/$NGINX
 ./configure и вставить строчку, скопированную из nginx -V, в конце добавить модуль:
 ./configure --prefix=/etc/nginx --sbin-path=/usr/sbin/nginx --modules-path=/usr/lib64/nginx/modules --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --pid-path=/var/run/nginx.pid --lock-path=/var/run/nginx.lock --http-client-body-temp-path=/var/cache/nginx/client_temp --http-proxy-temp-path=/var/cache/nginx/proxy_temp --http-fastcgi-temp-path=/var/cache/nginx/fastcgi_temp --http-uwsgi-temp-path=/var/cache/nginx/uwsgi_temp --http-scgi-temp-path=/var/cache/nginx/scgi_temp --user=nginx --group=nginx --with-compat --with-file-aio --with-threads --with-http_addition_module --with-http_auth_request_module --with-http_dav_module --with-http_flv_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_mp4_module --with-http_random_index_module --with-http_realip_module --with-http_secure_link_module --with-http_slice_module --with-http_ssl_module --with-openssl=/root/openssl --with-http_stub_status_module --with-http_sub_module --with-http_v2_module --with-mail --with-mail_ssl_module --with-stream --with-stream_realip_module --with-stream_ssl_module --with-stream_ssl_preread_module --with-cc-opt='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector-strong --param=ssp-buffer-size=4 -grecord-gcc-switches -m64 -mtune=generic' --add-module=/opt/lib/ngx_pagespeed
 make modules && make install && service nginx restart  
 
  
 если ругается на openssl:
 в файле nginx-source/auto/options
 USE_OPENSSL=YES OPENSSL=/root/openssl OPENSSL_OPT="no-ssl2 no-ssl3 -fPIC"
 
 
 pagespeed
 /etc/nginx/conf.d/pagespeed.cfg - настройки модуля pagespeed
 
 
  
 4) Установка PHP7
 а)  
 rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
 rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
 yum update
 yum install -y php70w php70w-opcache php70w-fpm php70w-gd php70w-mcrypt php70w-mysqlnd php70w-odbc php70w-pdo php70w-pecl-apcu php70w-xml php70w-mbstring  php70w-soap  
 
  
 systemctl enable php-fpm && systemctl start php-fpm
 
  
 б)
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
 
  
 5) Установка Mariadb
 а) добавить репозитарий
 tee /etc/yum.repos.d/Mariadb.repo <<-'EOF'
\ # http://mariadb.org/mariadb/repositories/
 [mariadb]
 name = MariaDB
 baseurl = http://yum.mariadb.org/10.1/centos7-amd64
 gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
 gpgcheck=1
 EOF
 
  
 б) установить софт
 yum -y install mariadb-server mariadb phpmyadmin mysqltuner &&
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
   
 chown -R nginx:nginx /var/lib/php/session /var/lib/php/wsdlcache /home/www /var/cache/nginx/pagespeed
 

 
   
    
 10) разное
 запускать только в папке сайта - устанавливает права 755 на категории, 644 на файлы
 find ./ -type d|xargs chmod 755 && find ./ -type f |xargs chmod 644
 
   
  
 пережать изображения в папке (запускать в той папке, в которой нужно пережать)
 find -type f -name "*.jpg" -exec jpegoptim --strip-all --max=90 {} \;
 
 
