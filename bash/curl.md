curl
========================
### download file from google drive
	curl https:/site.extremecentr.esclick.me/BqXq3pfZJJuu -L | egrep "https:\/\/drive\.google\.com\/file\/d\/(\w|-){26,}\/view"

### download specific file behind the form

curl -c cookie https://sva.kiev.ua$FILE