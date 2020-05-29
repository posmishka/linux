nginx.conf
=====
    gzip_types
        text/cache-manifest
        text/plain
        text/css
        text/xml
        text/vcard
        text/vnd.rim.location.xloc
        text/vtt
        text/x-component
        text/x-cross-domain-policy
        image/bmp
        image/x-icon
        image/svg+xml
        font/opentype
        application/atom+xml
        application/ld+json
        application/manifest+json
        application/x-javascript
        application/json
        application/xml
        application/rss+xml
        application/vnd.geo+json
        application/vnd.ms-fontobject
        application/javascript
        application/x-font-ttf
        application/font-woff
        application/x-web-app-manifest+json
        application/xhtml+xml;


    brotli_static off;
    brotli on;
    brotli_types text/plain text/css application/json image/svg+xml font/opentype  application/x-javascript text/xml application/xml application/xml+rss application/javascript application/x-font-ttf application/font-woff image/x-icon;
    brotli_buffers 128 16k;
    brotli_min_length 500;
    brotli_comp_level 9;

    # Logs

    log_format main_ext '$remote_addr - $remote_user [$time_local] "$request" ' '$status $body_bytes_sent "$http_referer" ' '"$http_user_agent" "$http_x_forwarded_for" ' '"$host" sn="$server_name" ' 'rt=$request_time ' 'ua="$upstream_addr" us="$upstream_status" ' 'ut="$upstream_response_time" ul="$upstream_response_length" ' 'cs=$upstream_cache_status' ;

    access_log off;
    error_log /var/log/nginx/error.log crit;

    # Cache

    proxy_send_timeout 300s;
    proxy_read_timeout 300s;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    include /etc/nginx/conf.d/*.conf;
    include /home/insecret/config/*.nginx;
}
