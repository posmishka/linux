troubleshoot
============

### проверка активных соединений

    ss -t -a -n | grep :443 | grep -i est | wc -l