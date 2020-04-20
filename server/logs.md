logs
======

https://stackify.com/syslog-101/  
http://www.rabbitmq.com/

### logwatch
    apt-get install logwatch


vim /etc/cron.daily/00logwatch

Добавьте следующую строку в файл cron:

/usr/sbin/logwatch --output mail --mailto you@example.com --detail high

### **syslog-ng**
    https://github.com/syslog-ng/syslog-ng
 
### **Elastic**  
    https://github.com/elastic/elasticsearch  
    https://github.com/elastic/kibana

### **graylog**
    https://www.graylog.org/

### **nagios**

    https://www.nagios.com/products/nagios-core/
    
### **papertrail** 
cloud  

    https://papertrailapp.com/