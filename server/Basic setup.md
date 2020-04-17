Basic setup
========================
+ [] **Update and install software**  
`yum update && yum -y install epel-release && \`  
`yum -y install htop atop mlocate mc wget curl fail2ban vim certbot net-tools vsftp.d db4-utils mc zip unzip`

   
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
+ [ ] Create a new user  
`username=yourname`
+ [ ] adduser $username
+ [ ] passwd $username
+ [ ] visudo - *adduser under the root to give him sudo access*  
`root    ALL=(ALL)       ALL`  
`yourname sasha_fox       ALL=(ALL)       ALL`

+ [ ] change ssh config  
*prevent root from entering, changing ssh port, allowing new user to enter*
```
 sed -i 's/^.*Port .*/Port 29920/g' /etc/ssh/sshd_config && \
 sed -i 's/^.*PermitRootLogin yes/PermitRootLogin no/g' /etc/ssh/sshd_config && \
 echo -e "\nAllowUsers $username" >> /etc/ssh/sshd_config && \
 systemctl restart sshd
```
+ [ ] check if you can connect in the new ssh window  
 `ssh -p29920 yourname@domain `
 
+ [ ] check if you have a root  
`sudo -i` 
  
+ [ ] generate public key and push it to the server  
`ssh-keygen`  
`cat /home/user/.ssh/id_rsa.pub >> yourname@domain:/home/user/.ssh/authorized_key`

+ [ ] add notification on root login  
`vi .bashrc`  
```echo 'ALERT - SSH root shell access found on '$HOSTNAME' on:' `date` `who` | mail -s "Alert: SSH root shell access" your@mail.co```