fastopen
========

https://github.com/yuryu/tfoecho/

You need to have linux kernel at least 3.7.

Edit /etc/sysctl.conf and add the following line to its end of file

   net.ipv4.tcp_fastopen = 3

sysctl -p

