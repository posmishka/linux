lvm
===

pvcreate /dev/sdb
vgcreate dbvg /dev/sdb
lvcreate -v -W y -Z y -l 100%VG -n lv_db dbvg
mkfs.ext4 /dev/mapper/dbvg-lv_db <---Вот тут вопрос. Может под БД xfs лучше?
echo "/dev/mapper/dbvg-lv_db /var/lib/mysql  ext4  defaults  1 2" >> /etc/fstab
mount /var/lib/mysql