ps / pidoff / pmap
==




`ps -ylC <procname>`  


RSS - resident set size, the non-swapped physical memory that a task has used (in kilobytes)
size - approximate amount of swap space that would be required if the process were to dirty all writable pages and then be swapped out. This number is very rough!

`pidof php-fpm | xargs pmap -d | grep '^mapped' | awk '{print $4}' | sed 's/K//' | perl -e 'do { $a+=$_; $b++ } for <>;print $a/1024, " mb\n", $a/1024/$b, " mb\n"'`


pmap
report memory map of a process


ps_mem

`for i in $(pgrep php-fpm); do echo "child $i"; ps_mem -s -p $i; done;`


<https://stackoverflow.com/questions/131303/how-to-measure-actual-memory-usage-of-an-application-or-process?rq=1>