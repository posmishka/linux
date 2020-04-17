Basic setup
========================
+ [] **Update and install software**

yum update && yum -y install epel-release && \
yum -y install htop atop mlocate mc wget curl fail2ban vim certbot net-tools vsftp.d db4-utils mc zip unzip

   
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

## **Setup SSH**
+ [ ] adduser %username%
+ [ ] passwd %username%
+ [ ] visudo - *adduser under the root*
```
 root    ALL=(ALL)       ALL
 sasha_fox       ALL=(ALL)       ALL
```
+ [ ] change ssh config  
*prevent root from entering, changing ssh port, allowing new user to enter
 порт обязательно нужно указать тот же, что указан в firewall.
 sed -i 's/^.*Port .*/Port 29920/g' /etc/ssh/sshd_config && \
 sed -i 's/^.*PermitRootLogin yes/PermitRootLogin no/g' /etc/ssh/sshd_config && \
 echo -e "\nAllowUsers alpi" >> /etc/ssh/sshd_config && \
 systemctl restart sshd
 в новом окне проверить доступ пользователя к серверу:
 ssh -p29920 sasha_fox@37.48.90.188  
 если всё успешно - проверить доступ через sudo :
 sudo htop
 для перехода в режим выполнения всех команд от root :  
 sudo -i
 
  
 в) настроить доступ по ключам, отключить доступ по паролям (опционально)
 для linux :
 ssh-keygen
 cat /home/user/.ssh/id_rsa.pub >> user@domain:/home/user/.ssh/authorized_key
 
