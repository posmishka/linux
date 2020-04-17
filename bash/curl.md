curl
====
Manual

	https://curl.haxx.se/docs/httpscripting.html


Login and password from form: 

	curl -c cookie -F "login=name" -F password=pass" https://site.com

OR

	curl -d "username=admin&password=admin&submit=Login" --dump-header headers http://localhost/Login
	curl -L -b headers http://localhost/
