site-migration
==============

```
# LOCAL_SERVER
LOCALDIR=/home/www
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
[[ ! -d ${LOCALDIR}/sql ]] || mkdir ${LOCALDIR}/sql

mysqldump --add-drop-table --single-transaction -u ${DBU1} -p${DBP1} ${DBN1} > ${LOCALDIR}/sql/${DBN1}.sql

rsync -av --delete-during -compress-level=9 --chown=${CHUSER}:${CHUSER} -e "ssh -p ${POR}" ${LOCALDIR}/{$SITE1} ${USER}@${HOST}:${REMOTEDIR}/www/${SITE1}

rsync -av -compress-level=9 -e "ssh -p "$PORT"" "$LOCALDIR"/sql/ "$USER"@"$HOST":/home/insecret/www/sql/
rsync -av -compress-level=9 -e "ssh -p ${PORT}" /etc/ ${USER}@${HOST}:/home/insecret/www/etc/

```
