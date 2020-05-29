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
#    add_header Feature-Policy "midi none;microphone none;camera none;";
```

## static

/etc/nginx/conf.d/static.inc


## prestashop 1.6