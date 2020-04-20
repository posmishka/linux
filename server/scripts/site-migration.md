site-migration
==============

```
echo '
#!/bin/sh

# LOCAL_SERVER
WORKDIR=/home/username/www
SITE1=site.ua
DBN=db_name
DBU=db_user
DBP=db_password

#REMOTE_SERVER
PORT=22
USER=user
HOST=1.2.3.4

#SITE_MOVEMENT
mkdir $WORKDIR/sql
mysqldump -u $DBU -p$DBP $DBN > $WORKDIR/sql/$DBN.sql
rsync -avv --delete-during -compress-level=9 -e "ssh -p $PORT" $WORKDIR/$SITE1/ $USER@$HOST:~/$SITE1/
rsync -avv -compress-level=9 -e "ssh -p $PORT" $WORKDIR/sql/ $USER@$HOST:~/sql/
' > sync.sh
```
