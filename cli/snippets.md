snippets
==

### pv - the progress bar
pv mydump.sql.gz | gunzip | mysql -u root -p basename

### inode economy while moving files
*creates hardlinks*

cp -rl ./source ./destination && rm -rf ./source

### permissions
find . -type d -exec chmod 755 -- {} + 
find . -type f -exec chmod 644 -- {} + 

### creating directories from file
cat foo.txt | xargs -I % sh -c 'echo %; mkdir %'