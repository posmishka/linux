phpmyadmin
==========

#### save version
```
DATA="$(wget https://www.phpmyadmin.net/home_page/version.txt -q -O-)"
URL="$(echo $DATA | cut -d ' ' -f 3)"
VER="$(echo $DATA | cut -d ' ' -f 1)"
```
#### download
    curl -o phpMyAdmin-${VER}-all-languages.tar.gz https://files.phpmyadmin.net/phpMyAdmin/${VER}/phpMyAdmin-${VER}-all-languages.tar.gz
    

#### extract

    tar xvf phpMyAdmin-${VER}-english.tar.gz
OR

    tar xvf phpMyAdmin-${VER}-all-languages.tar.gz
    
 #### move to /usr/share/phpmyadmin
 
    rm phpMyAdmin-*.tar.g
    sudo mv phpMyAdmin-*/ /usr/share/phpmyadmin
    
#### create directories

    sudo mkdir -p /var/lib/phpmyadmin/tmp
    sudo chown -R apache:apache /var/lib/phpmyadmin