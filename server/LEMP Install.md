LEMP Install
========================

Table of Contents

1. Nginx
    1. Install Dev Tools
    2. Setting variables
    3. Installing basic nginx
2. PHP7
3. MariaDB


# Nginx

*we will build the most recent version from source with custom modules to have http/2 enabled on CentOS7*  

## Install Dev Tools
we will need to remove them adter the building process

	yum -y groupinstall 'Development Tools'
	yum -y install wget openssl-devel libxml2-devel libxslt-devel gd-devel perl-ExtUtils-Embed GeoIP-devel

## Setting variables  

we will use latest openssl 1.0.2 branch from www.openssl.org/source/ 

	OPENSSL="openssl-1.0.2k"

nginx is the last stable from https://nginx.org/en/download.html 
	
	NGINX="nginx-1.16.1"

## Installing basic nginx

> PLACEHOLDER 

# PHP7

we will use custom repo for php 

	rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
	yum update
	yum install -y php70w php70w-opcache php70w-fpm php70w-gd php70w-mcrypt php70w-mysqlnd php70w-odbc php70w-pdo php70w-pecl-apcu php70w-xml php70w-mbstring  php70w-soap  
	 

 systemctl enable php-fpm && systemctl start php-fpm

 chown -R nginx:nginx /var/lib/php/session /var/lib/php/wsdlcache /home/www /var/cache/nginx/pagespeed
