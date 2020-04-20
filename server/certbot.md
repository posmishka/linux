certbot
=======

## certbot nginx plugin 
source: https://certbot.eff.org/lets-encrypt/centosrhel7-nginx.html

**install**
```
$ yum -y install yum-utils
$ yum-config-manager --enable rhui-REGION-rhel-server-extras rhui-REGION-rhel-server-optional
$ yum install certbot python2-certbot-nginx
```
**usage**
certbot --nginx certonly

certbot --nginx certonly

## old method

    $SITE=site.com

**add to nginx config (сайт должен быть доступен по 80 порту)
location /.well-known/acme-challenge { alias /home/www/.well-known/acme-challenge; }
nginx -s reload .
certbot certonly -a webroot --webroot-path /home/www/ -d $SITE -d www.$SITE --server https://acme-v01.api.letsencrypt.org/directory

openssl dhparam -out /etc/letsencrypt/live/$SITE/dhparam.pem 2048

sed(s/domain-in-cfg/newdomain/) ?

** вариант для всех доменов:
certbot renew
--force = принудительное обновление
--dry-run - тестовый прогон

## APACHE
```
sudo apt-get install apache2 
python-letsencrypt-apache
certbot --apache
```
