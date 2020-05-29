site-migration
==============

```
# LOCAL_SERVER
WORKDIR=/home/www
REMOTEDIR=/home/user
CHUSER=user

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

mysqldump --add-drop-table --single-transaction -u ${DBU1} -p${DBP1} ${DBN1} > ${WORKDIR}/sql/${DBN1}.sql

rsync -av --delete-during -compress-level=9 --chown=${CHUSER}:${CHUSER} -e "ssh -p ${POR}" ${WORKDIR}/{$SITE1}/public_html/ "$USER"@"$HOST":/home/insecret/www/${SITE1}

rsync -av -compress-level=9 -e "ssh -p "$PORT"" "$WORKDIR"/sql/ "$USER"@"$HOST":/home/insecret/www/sql/
rsync -av -compress-level=9 -e "ssh -p ${PORT}" /etc/ ${USER}@${HOST}:/home/insecret/www/etc/

```
