includes
========

## ssl
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