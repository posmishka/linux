shell
=========

**shell scripting**

https://en.terminalroot.com.br/45-examples-of-variables-and-arrays-in-shell-script/

падать при первом возврате не 0 команды  

    set -ex


**Parameter expansion**

    https://wiki.bash-hackers.org/syntax/pe

**creating binary from sh script**  

    https://linux.die.net/man/1/shc
    
**convert codepage**

    recode -f /QP..utf8
    
 **remove double quotes**
 
    echo "$opt" | sed -e 's/^"//' -e 's/"$//'
    B=$(tr --delete '\"' <<< $A)