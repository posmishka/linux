ps / pidoff
==




`ps -ylC <procname>`  


RSS - resident set size, the non-swapped physical memory that a task has used (in kilobytes)


`pidof php-fpm | xargs pmap -d | grep '^mapped' | awk '{print $4}' | sed 's/K//' | perl -e 'do { $a+=$_; $b++ } for <>;print $a/1024, " mb\n", $a/1024/$b, " mb\n"'`