config php
==========

    location ~ \.php$ {

        try_files $fastcgi_script_name /index.php$uri&$args =404;
        fastcgi_index  index.php;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;

        include fastcgi_params;

        fastcgi_pass   unix:/var/run/php-fpm.sock;
        fastcgi_param  HTTPS on;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        fastcgi_param  PATH_TRANSLATED  $document_root$fastcgi_script_name;
        fastcgi_param  HTTP_MOD_REWRITE On;
        fastcgi_keep_conn on;
        fastcgi_send_timeout 300s;
        fastcgi_read_timeout 300s;
        fastcgi_buffer_size 256k;
        fastcgi_buffers 256 16k;
        fastcgi_busy_buffers_size 256k;
        fastcgi_cache_valid 200 301 302 1h;
        fastcgi_cache_valid 404 500 501 502 503 504 505 506 507 509 510 1m;
        fastcgi_cache_valid any 1m;

   # Temp file tweak
        fastcgi_max_temp_file_size 0;
        fastcgi_temp_file_write_size 256k;