certbot
=======

 г) certbot, сертификаты ssl
 команда для выпуска сертификата:
 certbot certonly -a webroot --webroot-path /home/www/ -d site.com -d www.site.com --server https://acme-v01.api.letsencrypt.org/directory
 
  
 генерация DH-сертификата для ужесточения безопасности ssl
 openssl dhparam -out /etc/letsencrypt/live/glavzavhoz.ru/dhparam.pem 2048
