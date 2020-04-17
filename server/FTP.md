FTP
=============
# vsftpd

*the case is using virtual users for chrooted ftp directories*

> config placeholder

* [ ] Pam authentification

	tee /etc/pam.d/vsftpd.virtual <<-'EOF'
	auth required pam_userdb.so db=/etc/vsftpd/login
	account required pam_userdb.so db=/etc/vsftpd/login
	session required pam_loginuid.so
	EOF
в) занести в logins.txt пользователей и пароли
в папке users создать настройки для пользователей фтп (один пользователь
- одна настройка, задаётся папка, в которую у пользователя есть доступ)
useradd.sh