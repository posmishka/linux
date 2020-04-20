curl-solutions
========================
### download file from google drive
	curl https:/site.esclick.me/BqXq3pfZJJuu -L \
	| egrep "https:\/\/drive\.google\.com\/file\/d\/(\w|-){26,}\/view"


### find file in in raw mail and download from dropbox
	LINKS=$(tr --delete '=\n' < $MAILFILE | egrep -o "https:\/\/site\.esclick\.me\/\w{12}")
	
	for LINK in $LINKS                                                                                               
	do                                                                                                               
    URL=$(curl -Ls -o /dev/null -w %{url_effective} $LINK)                                                       
    [[ $URL == *dropboxusercontent*file ]] && $CURL $URL > "$FOLDER/filename.xls"                             
	done


### download specific file with cyrillic name behind the form

	FILE=$(curl -c cookie -X POST -F "login=login" -F "pass=password" https:/site.com -L \ 
	| iconv -f cp1251 -t utf8 - \
	| egrep -o 'Прайс.*\.htm' \
	| egrep -o "\/download\/f\/[0-9]{4,}\.htm")
	
	curl -b cookie https://site.com$FILE -o filename.xls
	
	
### test site response speed
`curl -w "Connect: %{time_connect} TTFB: %{time_starttransfer} Total time: %{time_total}" https://site.com`

simple script
```
#/bin/bash
SITE="$1"
for i in {1..5}; do curl -w "Connect: %{time_connect} TTFB: %{time_starttransfer} Total time: %{time_total}\n" -I https://108d.ru/contact-us >> ttfb; done
clear
echo "Result for site $SITE:"
cat ttfb | grep Connect:
rm ttfb
```
