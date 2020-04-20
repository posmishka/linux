snippets
==

### pv - the progress bar
pv mydump.sql.gz | gunzip | mysql -u root -p basename

### inode economy while moving files
creates hardlinks
cp -rl ./source ./destination rm -rf ./source
