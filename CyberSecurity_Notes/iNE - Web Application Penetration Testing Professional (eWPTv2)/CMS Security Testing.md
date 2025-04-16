# Security Testing Introduction
## Introduction to CMS Security Testing
![[Pasted image 20250225170941.png]]
![[Pasted image 20250225171310.png]]
![[Pasted image 20250225171643.png]]
![[Pasted image 20250225171957.png]]
![[Pasted image 20250225172104.png]]

## Introduction to WordPress Security Testing
![[Pasted image 20250225172355.png]]
![[Pasted image 20250225172509.png]]
![[Pasted image 20250225172720.png]]
![[Pasted image 20250225172807.png]]
![[Pasted image 20250225173037.png]]

# Information Gathering and Enumeration
## WordPress Version Enumeration
![[Pasted image 20250225173250.png]]
![[Pasted image 20250225173325.png]]
![[Pasted image 20250225173458.png]]

To start of with the Information Gathering Part : 
1. Try to find the Version of WordPress being used through navigating the Source Code and checking the `<meta>` tag
2. Then we could check for the `readme.html` or `license.txt` to get more information about the WordPress Versions
3. Then we could use Repeater and check for the Header like `Server` or `X-Powered-By` which would provide us with more information on WordPress or Server-Side Language
4. Then try to visit the Source Pages of the CMS : `/wp-login/` and `/wp-admin/`
5. We can also check for the file `changelog.txt` 
6. We could check for the XMLRPC File by visiting `/xmlrpc.php`

To install WPScan on Kali Linux, use the command : `sudo apt-get install wpscan`
To use WPScan, use the command : `wpscan --url http://domain.com/`

## Enumerating WordPress Users, Plugins & Themes
![[Pasted image 20250225174933.png]]
![[Pasted image 20250225175048.png]]![[Pasted image 20250225175118.png]]
![[Pasted image 20250225175223.png]]

For WordPress User Enumeration :
1. `curl -s -I -X GET https://domain.com/?author=1` - Check the `author=1` and change the id to check for different authors present in the webapp. Here we can also take the help of BurpSuite Intruder or Caido.
2. `curl https://domain.com/wwp-json/wp/v2/users` - Check for the users present and get their JSON Outputs.
3. Now we could also check for `/wp-login.php` and then directly check for the usernames as it might show you "Invalid Username" Error and then we could brute-force usernames and check for the actual valid usernames.
	![[Pasted image 20250225180537.png]]
4. ![[Pasted image 20250225180709.png]]Check for Plugins and Themes using the given Payloads and find out vulnerabilities in that.
5.  To enumerate the users using WPScan, use the command : `wpscan --url https://domain.com --enumerate u`
	![[Pasted image 20250225181410.png]]
6. ![[Pasted image 20250225181622.png]]

## Enumerating Hidden Files & Sensitive Information
![[Pasted image 20250225181919.png]]We can use Gobuster for Directory Brute-forcing : `gobuster dir --url https://domain.com/ --wordlist /usr/share/seclists/Discovery/Web-Content/CMS/wordpress.fuzz.tzt -b '404'` - Here `-b` tag is used for blacklisting a particular type of error `'404'`
![[Pasted image 20250225182821.png]]


## WordPress Enumeration with Nmap NSE Scripts
We could use the command : `sudo nmap -sS -sV domain.com` - Don't use the `http` or `https` here.

For WordPress Enumeration we could use a script named `http-wordpress-enum`, using the command : `sudo nmap -sS -sV --script=http-wordpress-enum domain.com`

We could also specify a  particular type that we're trying to find : `sudo nmap -sS -sV --script=http-wordpress=enum --script-args type="plugins" domain.com`

For enumerating any users, we could use the script `http-wordpress-users` and we could also specify the port number like `-p80,443`

# Vulnerability Scanning
![[Pasted image 20250226114146.png]]

To start with WPScan: 
- Get an account on the website of WPScan
- Then we get an API Token that we need to provide to the WPScan Tool.
- If we don't provide the API Token, then :  ![[Pasted image 20250226114643.png]]
- 

Command to enumerate plugins in WPScan : `wpscann --url https://domain.com/ --enumerate p`

# Authentication Attacks
## WP Brute-force Attacks
 In order to make a Brute-force attack, we will first enumerate users by the command : `wpscan --url https://domain.com/ --enumerate u`
 Then we will perform a Password Brute-force attack, by the command : `wpscan --url https:/domain.com/ -U <usernname> -P <path_to_wordlist>.txt`
 Then we could visit the website `https://domain.com/wp-login.php` and enter the enumerated username and password into it.
We can also use BurpSuite Intruder to brute-force the username and password.


# Exploiting Vulnerabilities
## WP Plugin - Arbitrary File Upload Vulnerability
At first, we'll try to check out for the vulnerability using `wpscan --url https://domain.com/ --enumerate p`
But to get a vulnerability report we need to specify the API-Token, by the command `wpscan --url https://domain.com/ --enumerate p --api-token "api-token"`
Then we will got Searchsploit to check for the vulnerability.


## WP Plugin - Stored XSS Vulnerability
At first, we'll try to check out for the vulnerability using `wpscan --url https://domain.com/ --enumerate p`
But to get a vulnerability report we need to specify the API-Token, by the command `wpscan --url https://domain.com/ --enumerate p --api-token "api-token"`
Then we will got Searchsploit to check for the vulnerability.

