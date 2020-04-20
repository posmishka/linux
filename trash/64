nginx
=====


 rpm -ivh http://nginx.org/packages/mainline/centos/7/SRPMS/$NGINX.el7.ngx.src.rpm && \
 sed -i "s|--with-http_ssl_module|--with-http_ssl_module --with-openssl=/opt/lib/$OPENSSL|g" /root/rpmbuild/SPECS/nginx.spec && \
 rpmbuild -ba /root/rpmbuild/SPECS/nginx.spec && \
 rpm -Uvh /root/rpmbuild/RPMS/x86_64/$NGINX.el7.centos.ngx.x86_64.rpm
 systemctl enable nginx


в) установка nginx с версией openssl 1.0.2j для поддержки http2
 mkdir -p /root/openssl && \
 wget https://www.openssl.org/source/$OPENSSL.tar.gz -O /root/openssl/$OPENSSL.tar.gz && \
 tar -zxvf /root/openssl/$OPENSSL.tar.gz -C /root/openssl
    
  
 
  
 г) опционально - установка модуля pagespeed google
 NGINX="nginx-1.11.13" && wget http://nginx.org/download/$NGINX.tar.gz ; tar xvzf $NGINX.tar.gz ; rm -rf $NGINX.tar.gz ; cd $NGINX
 bash <(curl -f -L -sS https://ngxpagespeed.com/install) -v 1.11.33.4
 
  
 nginx -V
 скопировать строчку после configure arguments:
  
 cd /root/$NGINX
 ./configure и вставить строчку, скопированную из nginx -V, в конце добавить модуль:
 ./configure --prefix=/etc/nginx --sbin-path=/usr/sbin/nginx --modules-path=/usr/lib64/nginx/modules --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --pid-path=/var/run/nginx.pid --lock-path=/var/run/nginx.lock --http-client-body-temp-path=/var/cache/nginx/client_temp --http-proxy-temp-path=/var/cache/nginx/proxy_temp --http-fastcgi-temp-path=/var/cache/nginx/fastcgi_temp --http-uwsgi-temp-path=/var/cache/nginx/uwsgi_temp --http-scgi-temp-path=/var/cache/nginx/scgi_temp --user=nginx --group=nginx --with-compat --with-file-aio --with-threads --with-http_addition_module --with-http_auth_request_module --with-http_dav_module --with-http_flv_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_mp4_module --with-http_random_index_module --with-http_realip_module --with-http_secure_link_module --with-http_slice_module --with-http_ssl_module --with-openssl=/root/openssl --with-http_stub_status_module --with-http_sub_module --with-http_v2_module --with-mail --with-mail_ssl_module --with-stream --with-stream_realip_module --with-stream_ssl_module --with-stream_ssl_preread_module --with-cc-opt='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector-strong --param=ssp-buffer-size=4 -grecord-gcc-switches -m64 -mtune=generic' --add-module=/opt/lib/ngx_pagespeed
 make modules && make install && service nginx restart  
 
  
 если ругается на openssl:
 в файле nginx-source/auto/options
 USE_OPENSSL=YES OPENSSL=/root/openssl OPENSSL_OPT="no-ssl2 no-ssl3 -fPIC"
 
 
 pagespeed
 /etc/nginx/conf.d/pagespeed.cfg - настройки модуля pagespeed
 



Deb пакет Nginx - сборка из исходников

https://techlist.top/nginx-deb-package-from-source/

https://blog.programs74.ru/how-to-enable-alpn-on-nginx/
 