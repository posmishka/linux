vim-tips
========

Убрать ДОС символы переноса строки:

:e ++ff=do:e ++ff=dos 

The :e ++ff=dos command tells Vim to read the file again, forcing  dos file format. Vim will remove CRLF and LF-only line endings, leaving  only the text of each line in the buffer.

then 

:set ff=unix 
and finally 
:wq 

:s/^M$//

(Press Ctrl+V Ctrl+M to insert that ^M.)


Интересно:
http://najomi.org/vim


DATABASE QUERY
https://habamax.github.io/2019/09/02/use-vim-dadbod-to-query-databases.html


vim-git
https://itnan.ru/post.php?c=1&p=261783