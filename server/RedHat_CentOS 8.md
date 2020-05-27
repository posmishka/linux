RedHat_CentOS 8
========

### hostname

hostnamectl set-hostname 
systemctl restart systemd-hostnamed

/etc/hosts file.

127.0.0.1	tecmint.rhel8

This automatically adds an entry by default to the /etc/hostname file.


https://developers.redhat.com/blog/2019/05/16/modular-perl-in-red-hat-enterprise-linux-8/

### CERTBOT
dnf config-manager --set-enabled PowerTools
dnf install -y certbot