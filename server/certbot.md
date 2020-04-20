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

## old meyt
 г) certbot, сертификаты ssl
 команда для выпуска сертификата:
 certbot certonly -a webroot --webroot-path /home/www/ -d site.com -d www.site.com --server https://acme-v01.api.letsencrypt.org/directory
 
 генерация DH-сертификата для ужесточения безопасности ssl
 openssl dhparam -out /etc/letsencrypt/live/glavzavhoz.ru/dhparam.pem 2048
