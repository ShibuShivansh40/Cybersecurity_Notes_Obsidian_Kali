## Default WordPress File Structure

WordPress can be installed on a Windows, Linux, or Mac OSX host. For this module, we will focus on a default WordPress installation on an Ubuntu Linux web server. WordPress requires a fully installed and configured LAMP stack (Linux operating system, Apache HTTP Server, MySQL database, and the PHP programming language) before installation on a Linux host. After installation, all WordPress supporting files and directories will be accessible in the webroot located at `/var/www/html`.

![[Pasted image 20250623181121.png]]

## WP Version - Source Code 
To get the Source Version Code, we use the command : `curl -s -X GET http://blog.inlanefreight.com | grep '<meta name="generator"'`

To check for the Version Number for Plugins : `curl -s -X GET http://blog.inlanefreight.com | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'wp-content/plugins/*' | cut -d"'" -f2`

To check for the Version Number for Themes : `curl -s -X GET http://blog.inlanefreight.com | sed 's/href=/\n/g' | sed 's/src=/\n/g' | grep 'themes' | cut -d"'" -f2`

To perform Plugins Active Enumeration : `curl -I -X GET http://blog.inlanefreight.com/wp-content/plugins/mail-masta`

## Directory Indexing
```shell-session
curl -s -X GET http://blog.inlanefreight.com/wp-content/plugins/mail-masta/ | html2text
```
Here html2text is the tool that converts HTML output to a nice readable format.

## User Enumeration
1. Check for the blogs or posts, where we could get parameters like ID, Usernames etc, so that we could enumerate them and check for other users too. The website URL would look like this : `http://blog.inlanefreight.com/?author=1`

2. The second method requires interaction with the `JSON` endpoint, which allows us to obtain a list of users. This was changed in WordPress core after version 4.7.1, and later versions only show whether a user is configured or not. Before this release, all users who had published a post were shown by default.
	**JSON Endpoint** : `curl http://blog.inlanefreight.com/wp-json/wp/v2/users | jq`


## Login
Once we are armed with a list of valid users, we can mount a password brute-forcing attack to attempt to gain access to the WordPress backend. This attack can be performed via the login page or the `xmlrpc.php` page.

To find Method Calls Available, we can use the command : `curl -X POST -d "<methodCall><methodName>system.listMethods</methodName><params></params></methodCall>" http://94.237.59.174:31080/xmlrpc.php`

