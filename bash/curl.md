curl
========================
### download file from google drive
	curl https:/site.extremecentr.esclick.me/BqXq3pfZJJuu -L \
	| egrep "https:\/\/drive\.google\.com\/file\/d\/(\w|-){26,}\/view"

### download specific file with cyrillic name behind the form

	FILE=$(curl -c cookie -X POST -F "login=login" -F "pass=password" https:/site.com -L \ 
	| iconv -f cp1251 -t utf8 - \
	| egrep -o 'Прайс.*\.htm' \
	| egrep -o "\/download\/f\/[0-9]{4,}\.htm")
	
	curl -b cookie https://site.com$FILE -o pricename.xls