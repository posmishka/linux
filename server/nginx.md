nginx
=====


 rpm -ivh http://nginx.org/packages/mainline/centos/7/SRPMS/$NGINX.el7.ngx.src.rpm && \
 sed -i "s|--with-http_ssl_module|--with-http_ssl_module --with-openssl=/opt/lib/$OPENSSL|g" /root/rpmbuild/SPECS/nginx.spec && \
 rpmbuild -ba /root/rpmbuild/SPECS/nginx.spec && \
 rpm -Uvh /root/rpmbuild/RPMS/x86_64/$NGINX.el7.centos.ngx.x86_64.rpm
 systemctl enable nginx
