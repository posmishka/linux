phpmyadmin
==========

phpmyadmin.inc



location /pma3388/ {

      #  auth_basic           "closed site";
      #  auth_basic_user_file ./pass/pma;

     alias /usr/share/phpMyAdmin/;

     location ~* ^/pma3388/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
        alias /usr/share/phpMyAdmin/$1;
     }

     location ~ \.php$ {

        fastcgi_split_path_info ^(.+\.php)(.*)$;
        fastcgi_pass   unix:/var/www/php-fpm/www-root.sock;
        fastcgi_index  index.php;
        fastcgi_param  HTTPS on;

        fastcgi_param SCRIPT_FILENAME $request_filename;

        fastcgi_param  HTTP_MOD_REWRITE On;

        include fastcgi_params;
        fastcgi_connect_timeout 300s;
        fastcgi_send_timeout 300s;
        fastcgi_read_timeout 12000s;
        fastcgi_ignore_client_abort off;

        fastcgi_buffer_size 16k;
        fastcgi_buffers 4 16k;


    }
}






location /phpmyadmin {
    alias /usr/share/phpMyAdmin/;

    location ~ /(libraries|setup) {
        return 404;
    }

    location ~ ^/phpmyadmin/(.*\.php)$ {
        alias /usr/share/phpMyAdmin/$1;
        fastcgi_pass 127.0.0.1:9000;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $request_filename;
    }
    location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
        alias /usr/share/phpMyAdmin/$1;
    }
}
