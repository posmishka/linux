Basic setup
========================

* [ ] **Install basic software**
``` 
yum update && yum -y install epel-release && \
yum -y install htop atop mlocate mc wget curl fail2ban vim certbot net-tools vsftp.d db4-utils mc zip unzip
```   
   
* [ ] **Setup firewall**  
*Assume that ssh port is 29920 instead of 22, opening ftp and web-server ports*
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
