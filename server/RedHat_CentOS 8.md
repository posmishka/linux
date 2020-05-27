RedHat_CentOS 8
========

### hostname
change hostname in /etc/sysctl.conf
kernel.hostname=sfpv-othe076.fz.fozzy.lan

hostnamectl set-hostname 
systemctl restart systemd-hostnamed


https://developers.redhat.com/blog/2019/05/16/modular-perl-in-red-hat-enterprise-linux-8/

### CERTBOT
dnf config-manager --set-enabled PowerTools
dnf install -y certbot