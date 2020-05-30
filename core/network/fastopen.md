fastopen
========

https://github.com/yuryu/tfoecho/

**You need to have linux kernel at least 3.7**

 $ vim /etc/sysctl.conf 
   
       net.ipv4.tcp_fastopen = 3
    
 $ sysctl -p



$ vim /etc/rc.local

    echo 3 > /proc/sys/net/ipv4/tcp_fastopen



ip tcp_metrics

grep '^TcpExt:' /proc/net/netstat | cut -d ' ' -f 87-92 | column -t