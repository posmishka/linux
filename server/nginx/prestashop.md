prestashop
==========

### 1.6

/etc/nginx/conf.d/prestashop16.inc
```
location ~ \.tpl$ { deny all; return 404; }

rewrite ^/[a-zA-Z][a-zA-Z]/index.php(.*)$ /index.php$1;
rewrite ^/api/?(.*)$ /webservice/dispatcher.php?url=$1 last;
rewrite ^/([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.jpg$ /img/p/$1/$1$2$3.jpg last;
rewrite ^/([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.jpg$ /img/p/$1/$2/$1$2$3$4.jpg last;
rewrite ^/([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.jpg$ /img/p/$1/$2/$3/$1$2$3$4$5.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.jpg$ /img/p/$1/$2/$3/$4/$1$2$3$4$5$6.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.jpg$ /img/p/$1/$2/$3/$4/$5/$1$2$3$4$5$6$7.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.jpg$ /img/p/$1/$2/$3/$4/$5/$6/$1$2$3$4$5$6$7$8.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.jpg$ /img/p/$1/$2/$3/$4/$5/$6/$7/$1$2$3$4$5$6$7$8$9.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.jpg$ /img/p/$1/$2/$3/$4/$5/$6/$7/$8/$1$2$3$4$5$6$7$8$9$10.jpg last;
rewrite ^/c/([0-9]+)(\-[\.*_a-zA-Z0-9-]*)(-[0-9]+)?/.+\.jpg$ /img/c/$1$2$3.jpg last;
rewrite ^/c/([a-zA-Z_-]+)(-[0-9]+)?/.+\.jpg$ /img/c/$1$2.jpg last;
rewrite ^/images_eei?([^/]+)\.(jpe?g|png|gif)$ /js/jquery/plugins/fancybox/images/$1.$2 last;
rewrite ^/page-not-found$ /index.php?controller=404 last;

rewrite ^/([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.webp$ /img/p/$1/$1$2$3.webp last;
rewrite ^/([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.webp$ /img/p/$1/$2/$1$2$3$4.webp last;
rewrite ^/([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.webp$ /img/p/$1/$2/$3/$1$2$3$4$5.webp last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.webp$ /img/p/$1/$2/$3/$4/$1$2$3$4$5$6.webp last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.webp$ /img/p/$1/$2/$3/$4/$5/$1$2$3$4$5$6$7.webp last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.webp$ /img/p/$1/$2/$3/$4/$5/$6/$1$2$3$4$5$6$7$8.webp last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.webp$ /img/p/$1/$2/$3/$4/$5/$6/$7/$1$2$3$4$5$6$7$8$9.webp last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])(\-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+\.webp$ /img/p/$1/$2/$3/$4/$5/$6/$7/$8/$1$2$3$4$5$6$7$8$9$10.webp last;
rewrite ^/c/([0-9]+)(\-[\.*_a-zA-Z0-9-]*)(-[0-9]+)?/.+\.webp$ /img/c/$1$2$3.webp last;
rewrite ^/c/([a-zA-Z_-]+)(-[0-9]+)?/.+\.webp$ /img/c/$1$2.webp last;

#Advaecee ieareh ilock options
#location /as4_seositemap-1.xml {
#    rewrite ^(.*)$ /modules/pm_advancedsearch4/sitemap/seositemap.xml break;
#}

location /as4_seositemap {
    rewrite ^/as4_seositemap-([0-9]+).xml$ /modules/pm_advancedsearch4/sitemap/seositemap-$1.xml break;
}

#next line is PSCSX-2790 bug workaround, fixed in 1.6.0.10
#rewrite ^/[a-zA-Z]+/img/cms/(.*)$ /img/cms/$1 break;

#rewrite "^/([a-z]{2})?/?s/([0-9]+)/([a-zA-Z0-9/_-]*)" /index.php?fc=module&module=pm_advancedsearch4&controller=advancedsearch4&isolang=$1&id_seo=$2&seo_url=$3 break;
#rewrite "^/ru/s/([0-9]+)/([a-zA-Z0-9/_-]*)" /index.php?fc=module&module=pm_advancedsearch4&controller=advancedsearch4&isolang=ru&id_seo=$1&seo_url=$2 break;
```

### 1.7
```
location /adminshop/ {
    if (!-e $request_filename) {
        rewrite ^/.*$ /adminshop/index.php last;
	}
    }


location /upload {
    location ~ \.php$ {
        deny all;
    }
}

location /img {
    location ~ \.php$ {
        deny all;
    }
}

location ~ ^/(app|bin|cache|classes|config|controllers|docs|localization|override|src|tests|tools|translations|travis-scripts|vendor|var)/ {
    deny all;
}

location ~ ^/modules/.*/vendor/ {
    deny all;
}

error_page 404 /index.php?controller=404;
rewrite ^/([0-9])(-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+.jpg$ /img/p/$1/$1$2$3.jpg last;
rewrite ^/([0-9])([0-9])(-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+.jpg$ /img/p/$1/$2/$1$2$3$4.jpg last;
rewrite ^/([0-9])([0-9])([0-9])(-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+.jpg$ /img/p/$1/$2/$3/$1$2$3$4$5.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])(-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+.jpg$ /img/p/$1/$2/$3/$4/$1$2$3$4$5$6.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])(-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+.jpg$ /img/p/$1/$2/$3/$4/$5/$1$2$3$4$5$6$7.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])(-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+.jpg$ /img/p/$1/$2/$3/$4/$5/$6/$1$2$3$4$5$6$7$8.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])(-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+.jpg$ /img/p/$1/$2/$3/$4/$5/$6/$7/$1$2$3$4$5$6$7$8$9.jpg last;
rewrite ^/([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])([0-9])(-[_a-zA-Z0-9-]*)?(-[0-9]+)?/.+.jpg$ /img/p/$1/$2/$3/$4/$5/$6/$7/$8/$1$2$3$4$5$6$7$8$9$10.jpg last;
rewrite ^/c/([0-9]+)(-[.*_a-zA-Z0-9-]*)(-[0-9]+)?/.+.jpg$ /img/c/$1$2$3.jpg last;
rewrite ^/c/([a-zA-Z_-]+)(-[0-9]+)?/.+.jpg$ /img/c/$1$2.jpg last;
rewrite ^/images_ie/?([^/]+).(jpe?g|png|gif)$ /js/jquery/plugins/fancybox/images/$1.$2 last; # testing
rewrite ^/order$ /index.php?controller=order last;      # testing

rewrite ^images_ie/?([^/]+)\.(jpe?g|png|gif)$ js/jquery/plugins/fancybox/images/$1.$2 last;
rewrite ^/api/?(.*)$ /webservice/dispatcher.php?url=$1 last;
rewrite ^(/install(?:-dev)?/sandbox)/(.*) /$1/test.php last;
```