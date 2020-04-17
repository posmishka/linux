Basic setup
========================

* [ ] **Install basic software**
``` 
yum update && yum -y install epel-release && \
yum -y install htop atop mlocate mc wget curl fail2ban vim certbot net-tools vsftp.d db4-utils mc zip unzip
```   
   
* [ ] **Setup firewall**  

 ```
 yum -y install firewalld && \
 systemctl start firewalld && \
 systemctl enable firewalld && \
 firewall-cmd --permanent --zone=public --add-service=http &&
 firewall-cmd --permanent --zone=public --add-service=https &&
 firewall-cmd --permanent --zone=public --add-port=443/tcp &&
 firewall-cmd --permanent --add-port=21/tcp &&
 firewall-cmd --permanent --add-service=ftp &&
 firewall-cmd --permanent --add-port=29920/tcp &&
 firewall-cmd --reload
``` 
 б) настройка firewall - доступ ftp, http, https, ssh. стандартный порт ssh - 22 - меняется на 29920