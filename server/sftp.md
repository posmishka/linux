sftp
====

Goal: Keep the user chroot but allow WRITE access to the relative chroot directory, without having to specific any path or cd anywhere.

`$ vim /etc/ssh/sshd_config`


comment string

`#Subsystem sftp /usr/lib/openssh/sftp-server`

add

`Subsystem sftp internal-sftp -f AUTH -l VERBOSE`
```
Match User sftpuser
    ChrootDirectory /home
    ForceCommand internal-sftp -d /sftpuser
    AllowTCPForwarding no
    X11Forwarding no
```

Once that is done you have to give the right permissions as said earlier, the root should own the parent(chroot) directory /home while the user should own the final(-d) directory /sftpuser. I am goin to assume that you have an sFTP users group called sftpusers, if not; just ommit the group from the next commands or replace it with the users instead (root in the first and sftpusers in the second). As we are using -R in the command line for inheritance, you will have to start with the root ownership before the user ownership as follows:

    sudo chown -R root:sftpusers /home

then for the user you can run:

    sudo chown -R sftpuser:sftpusers /home/sftpuser


(c) <https://serverfault.com/questions/910789/chroot-sftp-possible-to-allow-user-to-write-to-current-chroot-directory>