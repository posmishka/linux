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
    AllowAgentForwarding no
    AllowTCPForwarding no
    X11Forwarding no
```

Once that is done you have to give the right permissions as said earlier, the root should own the parent(chroot) directory /home while the user should own the final(-d) directory /sftpuser. I am goin to assume that you have an sFTP users group called sftpusers, if not; just ommit the group from the next commands or replace it with the users instead (root in the first and sftpusers in the second). As we are using -R in the command line for inheritance, you will have to start with the root ownership before the user ownership as follows:

    sudo chown -R root:sftpusers /home

then for the user you can run:

    sudo chown -R sftpuser:sftpusers /home/sftpuser


(c) <https://serverfault.com/questions/910789/chroot-sftp-possible-to-allow-user-to-write-to-current-chroot-directory>


### Where do I set up the file creation mask permissions for Secure FTP over SSH (SFTP)?

    ForceCommand internal-sftp -d /sftpuser -u 0002



umask description:

IIRC it uses the users login shell, but I think in non-interactive mode, which means $BASH_ENV is called to be sourced. If that's not the case (meaning it uses interactive mode), then it depends on if it uses the shell as login shell or not.
If it's a login shell in interactive mode, then the same $BASH_ENV will be sourced (in case of bash, ~/.bashrc),

else it's the sequence in that order:
* /etc/profile
* .bash_profile
* .bash_login
* .profile

More : https://linuxandevops.wordpress.com/2017/07/30/ssh-scp-sftp-connections-and-file-permissions-part-2/