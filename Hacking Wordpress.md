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
