lvm
===

```sh
pvcreate /dev/sdb
vgcreate dbvg /dev/sdb
lvcreate -v -W y -Z y -l 100%VG -n lv_db dbvg
mkfs.ext4 /dev/mapper/dbvg-lv_db <---Вот тут вопрос. Может под БД xfs лучше?
echo "/dev/mapper/dbvg-lv_db /var/lib/mysql  ext4  defaults  1 2" >> /etc/fstab
mount /var/lib/mysql
```

выбор фс
https://www.percona.com/blog/2018/07/03/linux-os-tuning-for-mysql-database-performance/
https://fuzzyblog.io/blog/mysql/2014/08/28/optimizing-your-filesystem-for-mysql.html

perfomance, journaling
https://serverfault.com/questions/363355/io-wait-causing-so-much-slowdown-ext4-jdb2-at-99-io-during-mysql-commit