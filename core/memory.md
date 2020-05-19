memory
==




`ps -ylC <procname>`  


RSS - resident set size, the non-swapped physical memory that a task has used (in kilobytes)
size - approximate amount of swap space that would be required if the process were to dirty all writable pages and then be swapped out. This number is very rough!

`pidof php-fpm | xargs pmap -d | grep '^mapped' | awk '{print $4}' | sed 's/K//' | perl -e 'do { $a+=$_; $b++ } for <>;print $a/1024, " mb\n", $a/1024/$b, " mb\n"'`


pmap
report memory map of a process


ps_mem

`for i in $(pgrep php-fpm); do echo "child $i"; ps_mem -s -p $i; done;`


<https://stackoverflow.com/questions/131303/how-to-measure-actual-memory-usage-of-an-application-or-process?rq=1v>




### Memory Consumption in Linux
<https://web.archive.org/web/20120520221529/http://emilics.com/blog/article/mconsumption.html>

```python
#! /usr/bin/python
# coding: utf-8
##-----------------------------------------------------------------------------
## pss.py --- Print the PSS (Proportional Set Size) of accessable processes
##                        copyright (C) 2012 Emil Norisky, all rights reserved.
##-----------------------------------------------------------------------------
import os, sys, re, pwd


##-----------------------------------------------------------------------------
def pss_main():
    '''
    Print the user name, pid, pss, and the command line for all accessable
    processes in pss descending order.
    '''
    # Get the user name, pid, pss, and the command line information for all
    # processes that are accessable. Ignore processes where the permission is
    # denied.
    ls = []   # [(user, pid, pss, cmd)]
    for pid in filter(lambda x: x.isdigit(), os.listdir('/proc')):
        try:
            ls.append((owner_of_process(pid), pid, pss_of_process(pid), cmdline_of_process(pid)))
        except IOError:
            pass

    # Calculate the max length of the user name, pid, and pss in order to
    # print them in aligned columns.
    userlen = 0
    pidlen = 0
    psslen = 0
    for (user, pid, pss, cmd) in ls:
        userlen = max(userlen, len(user))
        pidlen = max(pidlen, len(pid))
        psslen = max(psslen, len(str(pss)))
    
    # Get the width of the terminal.
    with os.popen('tput cols') as fp:
        term_width = int(fp.read().strip())
    
    # Print the information. Ignore kernel modules since they allocate memory
    # from the kernel land, not the user land, and PSS is the memory
    # consumption of processes in user land.
    fmt = '%%-%ds  %%%ds  %%%ds  %%s' % (userlen, pidlen, psslen)
    print(fmt % ('USER', 'PID', 'PSS', 'COMMAND'))
    for (user, pid, pss, cmd) in sorted(ls, lambda x, y: cmp(y[2], x[2])):
        if cmd != '':
            print((fmt % (user, pid, pss, cmd))[:term_width - 1])


##-----------------------------------------------------------------------------
def pss_of_process(pid):
    '''
    Return the PSS of the process specified by pid in KiB (1024 bytes unit)
    
    @param pid  process ID
    @return     PSS value
    '''
    with file('/proc/%s/smaps' % pid) as fp:
        return sum([int(x) for x in re.findall('^Pss:\s+(\d+)', fp.read(), re.M)])


##-----------------------------------------------------------------------------
def cmdline_of_process(pid):
    '''
    Return the command line of the process specified by pid.

    @param pid  process ID
    @return     command line
    '''
    with file('/proc/%s/cmdline' % pid) as fp:
        return fp.read().replace('\0', ' ').strip()


##-----------------------------------------------------------------------------
def owner_of_process(pid):
    '''
    Return the owner of the process specified by pid.

    @param pid  process ID
    @return     owner
    '''
    return pwd.getpwuid(os.stat('/proc/%s' % pid).st_uid).pw_name


##-----------------------------------------------------------------------------
if __name__ == '__main__':
    pss_main()

```

