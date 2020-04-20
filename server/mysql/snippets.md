snippets
========

исправить хост юзера в престашоп
use mysql;
UPDATE user SET host='localhost' where user='user';
UPDATE db SET host='localhost' where user='user';