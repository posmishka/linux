config
======
```sh
server {
    listen 80;
    server_name it-t.alpi.pp.ua;
    #server_name insecret.trade www.insecret.trade;
    return 301 https://it-t.alpi.pp.ua$request_uri;
    #return 301 https://insecret.trade$request_uri;
}

server {
    listen 443 ssl http2;
    #server_name insecret.trade www.insecret.trade;
    server_name it-t.alpi.pp.ua;

    #SSL
    ssl_certificate /etc/letsencrypt/live/it-t.alpi.pp.ua/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/it-t.alpi.pp.ua/privkey.pem;
#    ssl_certificate /etc/letsencrypt/live/insecret.trade/fullchain.pem;
#    ssl_certificate_key /etc/letsencrypt/live/insecret.trade/privkey.pem;
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;

    include /etc/nginx/conf.d/ssl.inc;
    include /etc/nginx/conf.d/headers.inc;
    include /etc/nginx/conf.d/static.inc;
    include /etc/nginx/conf.d/prestashop16.inc

    charset utf-8;
    root /home/insecret/www/insecret.trade;

    location / {
        index index.php;
        try_files $uri $uri/ /index.php$is_args$args;
    }

    client_max_body_size 100m;
    client_body_buffer_size 1m;
    client_header_buffer_size 2k;
    large_client_header_buffers 4 8k;

    location ~ \.php$ {
        fastcgi_pass    unix:/var/run/php-fpm.sock;
        fastcgi_index   index.php;
        fastcgi_keep_conn on;
        fastcgi_intercept_errors on;
        fastcgi_ignore_headers "Cache-Control" "Expires";
        fastcgi_param   SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include         fastcgi_params;

        fastcgi_connect_timeout 300s;
        fastcgi_send_timeout 300s;
        fastcgi_read_timeout 1200s;
        fastcgi_buffer_size 1m;
        fastcgi_buffers 8 8m;
        fastcgi_cache_valid 200 301 302 1h;
        fastcgi_cache_valid 404 500 501 502 503 504 505 506 507 509 510 1m;
        fastcgi_cache_valid any 1m;
    }

    access_log /home/insecret/logs/insecret.trade.access.log;
    error_log  /home/insecret/logs/insecret.trade.error.log;
}
```