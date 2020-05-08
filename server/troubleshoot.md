troubleshoot
============
## Rosources



mpstat
iostat
vmstat


## Network

### проверка активных соединений

    ss -t -a -n | grep :443 | grep -i est | wc -l
    
### подсчет соединений с ip-адресами
    netstat -an | grep -E '\:80|\:443'| awk '{print $5}' | grep -Eo '[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}' | sort | uniq -c | sort -n