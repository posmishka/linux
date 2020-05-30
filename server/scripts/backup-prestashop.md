backup-prestashop
======

```
#!/bin/sh

##  Backup to Google Drive. Author: Oleksii Pylypchuk 
##  github: https://github.com/alpi-ua/backup-site/
##  
##  This script is designed to upload daily backup of the wordpress site to the google drive
##  In case of fail email is sending to admin via mailx with log attached
##  You should download https://github.com/odeke-em/drive and specify backup.log, email for using this script
##
##  The crontab record is
##  10 5 * * * /path/to/script/backup-wordpress.sh > /path/to/backup.log 2>&1
##  Make sure the owner of the backup.log is the same who is running cron job

DATE_FORMAT='+[%d-%m-%Y] %H:%M:%S'

USER=insecret

site=insected.trade
workdir=/home/${USER}/backup
sitedir=/home/${USER}/www

mysqldb=insecret_trade
mysqluser=insecret_trade
mysqlpass=KdcCwfjgRDscz2YOBnMI2/Uh6pESulKT4nVqbQfM

backuplog=/home/${USER}/logs/${site}.backup.log
email=evgenij.sobolev@gmail.com

echo $(date "$DATE_FORMAT") "| Starting..."
echo $(date "$DATE_FORMAT") "| Backuping database"

[ -d ${workdir}/${site} ] || mkdir ${workdir}/${site}

mysqldump -u "$mysqluser" -p"$mysqlpass" "$mysqldb" > "$workdir"/"$site"/"$site".sql

    returncode=$?

    if [ $returncode -ne 0 ]
    then
        echo $(date "$DATE_FORMAT") "| Failed to create a database backup. Return code is "$returncode""
        echo "Error backuping "$site" database. mysqldump returned code $returncode" | mail -s "Error backuping DB "$site"" -a "$backuplog" "$email"
    else
        echo $(date "$DATE_FORMAT") "| Database backup created" 
    fi

[ -f ""$workdir"/"$site"/"$site".zip" ] && [ -f ""$workdir"/"$site"/"$site"-img.zip" ] &&
    echo $(date "$DATE_FORMAT") "| Moving the old backup" &&
    mv "$workdir"/"$site"/"$site".zip "$workdir"/"$site"/"$site".zip.old &&
    mv "$workdir"/"$site"/"$site"-img.zip "$workdir"/"$site"/"$site"-img.zip.old

echo $(date "$DATE_FORMAT") "| Archiving files and database"

zip -rq -x="$sitedir"/cache/smarty/\* -x="$sitedir"/img/p/\* -x="$sitedir"/upload/\* -x="$sitedir"/modules/expresscache/cache/\* "$workdir"/"$site"/"$site".zip "$sitedir"/ "$sitedir"/"$site".sql

    returncode=$?

    if [ $returncode -ne 0 ]
    then
        echo $(date "$DATE_FORMAT") "| Error creating zip file. "$workdir"/"$site"/"$site".zip.old will stay. Return code is "$returncode""       
        echo "Error when creating "$site" archieve. ZIP returned code $returncode" | mail -s "Error creating backup "$site"" -a "$backuplog" "$email"
        rm -rf "$workdir"/"$site"/"$site".zip
    else
        rm -rf "$workdir"/"$site"/"$site".sql
        rm -rf "$workdir"/"$site"/"$site".zip.old
        echo $(date "$DATE_FORMAT") "| Archive created. Old archive deleted"
    fi

echo $(date "$DATE_FORMAT") "| Archiving images"

zip -rq $workdir/$site/$site-img.zip $sitedir/img/p/

   returncode=$?

    if [ $returncode -ne 0 ]
    then
        echo $(date "$DATE_FORMAT") "| Error creating images archive. Return code "$returncode"" 
        echo "Error when creating "$site" archieve. ZIP returned code $returncode" | mail -s "Error creating backup "$site"" -a "$backuplog" "$email"