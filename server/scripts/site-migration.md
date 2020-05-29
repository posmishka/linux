site-migration
==============

```
# LOCAL_SERVER
WORKDIR=/home/www

SITE1=
DBN1=
DBU1=
DBP1=

#REMOTE_SERVER
PORT=29920
USER=root
HOST=185.197.160.194

#SITE_MOVEMENT
mkdir $WORKDIR/sql
mysqldump --add-drop-table --single-transaction -u "DBU1" -p"$DBP1" "$DBN1" > "$WORKDIR"/sql/"$DBN1".sql
mysqldump --add-drop-table --single-transaction -u "$DBU2" -p"$DBP2" "$DBN2" > "$WORKDIR"/sql/"$DBN2".sql
mysqldump --add-drop-table --single-transaction -u "$DBU3" -p"$DBP3" "$DBN3" > "$WORKDIR"/sql/"$DBN3".sql
rsync -av --delete-during -compress-level=9 --chown=insecret:insecret -e "ssh -p "$PORT"" "$WORKDIR"/"$SITE1"/public_html/ "$USER"@"$HOST":/home/insecret/www/${SITE1}
rsync -av --delete-during -compress-level=9 --chown=insecret:insecret -e "ssh -p "$PORT"" "$WORKDIR"/"$SITE2"/public_html/ "$USER"@"$HOST":/home/insecret/www/${SITE2}
rsync -av --delete-during -compress-level=9 --chown=insecret:insecret -e "ssh -p "$PORT"" "$WORKDIR"/"$SITE3"/public_html/ "$USER"@"$HOST":/home/insecret/www/${SITE3}

rsync -av -compress-level=9 -e "ssh -p "$PORT"" "$WORKDIR"/sql/ "$USER"@"$HOST":/home/insecret/www/sql/
rsync -av -compress-level=9 -e "ssh -p ${PORT}" /etc/ ${USER}@${HOST}:/home/insecret/www/etc/

```
