Centos 8
===============

rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm

dnf install -y https://rpms.remirepo.net/enterprise/remi-release-8.rpm

dnf module list php


php74,73,72 same time

dnf module enable php:remi-7.3 -y



php71

rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm && yum update

dnf install php71 php71-php-opcache php71-php-fpm php71-php-gd php71-php-mcrypt php71-php-mysqlnd php71-php-odbc php71-php-pdo php71-php-pecl-apcu php71-php-xml php71-php-mbstring


php.x86_64
php-bcmath.x86_64
php-cli.x86_64
php-common.x86_64
php-fedora-autoloader.noarch
php-fpm.x86_64
php-gd.x86_64
php-intl.x86_64
php-json.x86_64
php-mbstring.x86_64
php-mysqlnd.x86_64
php-odbc.x86_64
php-opcache.x86_64
php-pdo.x86_64
php-pear.noarch
php-pecl-apcu.x86_64
php-pecl-mcrypt.x86_64
php-pecl-zip.x86_64
php-process.x86_64
php-soap.x86_64
php-tidy.x86_64
php-xml.x86_64
php71.x86_64
php71-php-bcmath.x86_64
php71-php-cli.x86_64
php71-php-common.x86_64
php71-php-fpm.x86_64
php71-php-gd.x86_64
php71-php-intl.x86_64
php71-php-json.x86_64
php71-php-mbstring.x86_64
php71-php-mcrypt.x86_64
php71-php-mysqlnd.x86_64
php71-php-odbc.x86_64
php71-php-opcache.x86_64
php71-php-pdo.x86_64
php71-php-pecl-apcu.x86_64
php71-php-pecl-zip.x86_64
php71-php-soap.x86_64
php71-php-xml.x86_64
php71-runtime.x86_64
