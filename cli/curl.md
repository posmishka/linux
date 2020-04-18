curl
====
Manual

	https://curl.haxx.se/docs/httpscripting.html


Login and password from form: 

	curl -c cookie -F "login=name" -F password=pass" https://site.com

OR

	curl -d "username=admin&password=admin&submit=Login" --dump-header headers http://localhost/Login
	curl -L -b headers http://localhost/






If you are lazy, you can get google-chrome or firefox to do all the work for you.

    Right-click the form you want to submit and select Inspect (or Inspect Element for Firefox). This will open the DevTools panel.
    Select the Network tab in devtools and tick the Preserve log checkbox (Persist Logs for firefox).
    Submit the form and locate the entry with method POST (right-click on any column header and make sure Method is checked).
    Right click the line with POST, and select Copy > Copy as cURL.



chrome devtools: copy as cURL

Chrome will copy all the request data in cURL syntax.

Chrome uses --data 'param1=hello&param2=world' which you can make more readable by using a single -d or -F per parameter depending on which type of POST request you want to send, which can be either application/x-www-form-urlencoded or multipart/form-data accordingly.

This will be POST-ed as application/x-www-form-urlencoded (used for the majority of forms that don't contain file uploads):

curl http://httpbin.org/post \
    -H "User-Agent: Mozilla/2.2" \
    -d param1=hello \
    -d name=dinsdale

For a multipart/form-data POST use -F (typically used with forms that contain file uploads, or where order of fields is important, or where multiple fields with the same name are required):

curl http://httpbin.org/post \
    -H "User-Agent: Mozilla/2.2" \
    -F param1=hello \
    -F name=dinsdale \
    -F name=piranha

The User-Agent header is not normally needed, but I've thrown it in just in case. If you need a custom agent then you can avoid having setting it on every request by creating the ~/.curlrc file which contains e.g. User-Agent: "Mozilla/2.2"
