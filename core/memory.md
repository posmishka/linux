memory
==



### ps
`ps -ylC <procname>`  
`ps aux`

### pmap
report memory map of a process
`pidof php-fpm | xargs pmap -d | grep '^mapped' `

### ps_mem
Can determine how much RAM is used per program (not per process).

`for i in $(pgrep php-fpm); do echo "child $i"; ps_mem -s -p $i; done;`


### smem
Reports physical memory usage, taking shared  memory  pages into  account. Unshared  memory is reported as the USS (Unique Set Size).  Shared memory is divided evenly among the  processes sharing that memory. 

The unshared memory (USS) plus a process's proportion of shared memory is reported as the PSS (Proportional Set  Size). The USS and PSS only include physical memory usage. 

They do not include memory that has been swapped out to disk.

Memory can be reported by process, by user, by mapping, or  sys‐temwide. Both text mode and graphical output are available.


### pss.py


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

### Links
<https://stackoverflow.com/questions/131303/how-to-measure-actual-memory-usage-of-an-application-or-process?rq=1v>
<https://web.archive.org/web/20120520221529/http://emilics.com/blog/article/mconsumption.html>