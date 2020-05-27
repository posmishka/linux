install centos8
===============

rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm

dnf install -y https://rpms.remirepo.net/enterprise/remi-release-8.rpm

dnf module list php


php74,73,72 s



php71

rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm && yum update

dnf install php71 php71-php-opcache php71-php-fpm php71-php-gd php71-php-mcrypt php71-php-mysqlnd php71-php-odbc php71-php-pdo php71-php-pecl-apcu php71-php-xml php71-php-mbstring