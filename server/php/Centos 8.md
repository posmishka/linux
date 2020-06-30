Centos 8
===============

rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm


dnf install -y https://rpms.remirepo.net/enterprise/remi-release-8.rpm

dnf module list php


php74,73,72 same time

dnf module enable php:remi-7.3 -y

yum --disablerepo="*" --enablerepo="remi-safe" list available | more
yum --disablerepo="*" --enablerepo="remi-safe" search php

php71

rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm && yum update

dnf install php71 php71-php-opcache php71-php-fpm php71-php-gd php71-php-mcrypt php71-php-mysqlnd php71-php-odbc php71-php-pdo php71-php-pecl-apcu php71-php-xml php71-php-mbstring


php
php-bcmath
php-cli
php-common
php-fedora-autoloader.noarch
php-fpm
php-gd
php-intl
php-json
php-mbstring
php-mysqlnd
php-odbc
php-opcache
php-pdo
php-pear.noarch
php-pecl-apcu
php-pecl-mcrypt
php-pecl-zip
php-process
php-soap
php-tidy
php-xml

php71
php71-php-bcmath
php71-php-cli
php71-php-common
php71-php-fpm
php71-php-gd
php71-php-intl
php71-php-json
php71-php-mbstring
php71-php-mcrypt
php71-php-mysqlnd
php71-php-odbc
php71-php-opcache
php71-php-pdo
php71-php-pecl-apcu
php71-php-pecl-zip
php71-php-soap
php71-php-xml
php71-runtime
