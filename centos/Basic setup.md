Basic setup
========================

**Install basic software**
``` 
yum update && yum -y install epel-release && \
yum -y install htop atop mlocate mc wget curl fail2ban vim certbot net-tools vsftp.d db4-utils mc zip unzip
```
 
 б) настройка firewall - доступ ftp, http, https, ssh. стандартный порт ssh - 22 - меняется на 29920