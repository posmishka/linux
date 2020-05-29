includes
========

## ssl
/etc/nginx/conf.d/ssl.inc
```
ssl_session_timeout 10m;
ssl_session_cache shared:SSL:50m;
ssl_protocols TLSv1.3 TLSv1.2;
ssl_prefer_server_ciphers on;
ssl_ciphers EECDH:+AES256:-3DES:RSA+AES:RSA+3DES:!NULL:!RC4;
resolver 1.1.1.1 8.8.8.8 valid=300s;
ssl_stapling on;
ssl_stapling_verify on;
resolver_timeout 10s;
```

## headers

/etc/nginx/conf.d/headers.inc
```
add_header Cache-Control public;
add_header Strict-Transport-Security "max-age=63072000; includeSubdomains; preload";
add_header X-XSS-Protection "1; mode=block";
add_header X-Frame-Options "SAMEORIGIN";
add_header Referrer-Policy "no-referrer-when-downgrade";
add_header X-Content-Type-Options nosniff;

#add_header Content-Security-Policy "default-src 'self';";
#add_header Feature-Policy "midi none;microphone none;camera none;";
#add_header Access-Control-Allow-Origin *;
```
<https://m.habr.com/ru/company/hosting-cafe/blog/315802/>
## static

/etc/nginx/conf.d/static.inc
```
location ~ /\.ht { deny  all; }
location /robots.txt { allow all; log_not_found off; access_log off; }
location ~ \.(htaccess|yml|log|twig|sass|git|tpl)$ { deny all; }

location ~* ^.+\.jpg  { access_log off; error_log off; expires max; gzip off; add_header Cache-Control "public";}
location ~* ^.+\.jpeg { access_log off; error_log off; expires max; gzip off; add_header Cache-Control "public";}
location ~* ^.+\.gif  { access_log off; error_log off; expires max; gzip off; add_header Cache-Control "public";}
location ~* ^.+\.ico  { access_log off; error_log off; expires max; gzip off; add_header Cache-Control "public";}
location ~* ^.+\.png  { access_log off; error_log off; expires max; gzip off; add_header Cache-Control "public";}
location ~* ^.+\.css  { access_log off; expires 31d; add_header Vary Accept-Encoding; add_header Cache-Control "public, must-revalidate, proxy-revalidate";}
location ~* ^.+\.(svg|eot|otf|ttf|woff(?:2)?)  { access_log off; error_log off; expires max; add_header Cache-Control "public";}
``` 
## cloudflare
/etc/nginx/conf.d/cloudflare.inc
```
ssl_client_certificate /etc/nginx/certs/cloudflare.crt;
ssl_verify_client on;

location ~* \.(eot|otf|ttf|woff|woff2)$ {
    add_header Access-Control-Allow-Origin *;
}

set_real_ip_from 173.245.48.0/20;
set_real_ip_from 103.21.244.0/22;
set_real_ip_from 103.22.200.0/22;
set_real_ip_from 103.31.4.0/22;
set_real_ip_from 141.101.64.0/18;
set_real_ip_from 108.162.192.0/18;
set_real_ip_from 190.93.240.0/20;
set_real_ip_from 188.114.96.0/20;
set_real_ip_from 197.234.240.0/22;
set_real_ip_from 198.41.128.0/17;
set_real_ip_from 162.158.0.0/15;
set_real_ip_from 104.16.0.0/12;
set_real_ip_from 172.64.0.0/13;
set_real_ip_from 131.0.72.0/22;
set_real_ip_from 2400:cb00::/32;
set_real_ip_from 2606:4700::/32;
set_real_ip_from 2803:f800::/32;
set_real_ip_from 2405:b500::/32;
set_real_ip_from 2405:8100::/32;
set_real_ip_from 2a06:98c0::/29;
set_real_ip_from 2c0f:f248::/32;
real_ip_header CF-Connecting-IP;
```
