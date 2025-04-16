![[Pasted image 20241020232507.png]]
![[Pasted image 20241020232716.png]]
**What Information are we looking for ?**
![[Pasted image 20241020232807.png]]
**Passive Information Gathering**
![[Pasted image 20241020232939.png]]
**Active Information Gathering**
![[Pasted image 20241020233019.png]]
**OWASP WSTG**
A good checklist : https://github.com/tanprathan/OWASP-Testing-Checklist

# Finding Ownership & IP Addresses

#### **WHOIS**
![[Pasted image 20241021004036.png]]

```
To get the information about the ownership of the domain, we can use the command : whois <target_website>
```
![[Pasted image 20241021004330.png]]
```
To know about the IP Addresses of the domain servers, we use the command : host <target_url>
```
Method use to extract details up are : **whois url** -> **host host_name** -> **whois IP_Address**

Online tools to gather information regarding the Web Apps or Domains : 
1.  https://whois.domaintools.com/


### Website Fingerprinting with Netcraft
To use Netcraft, we need to visit the website : www.netcraft.com/
It tell us a lot about the website like SSL Certificates, Background, Hosting History, Network Information etc. It also tell us about the IP Delegation. It gives us a brief knowledge about what the site is running.

### Passive DNS Enumeration
**DNS**
![[Pasted image 20241022002410.png]]
**DNS Records**
![[Pasted image 20241022002852.png]]
**DNS Enumeration**
![[Pasted image 20241022002343.png]]
Tools that we are going to use during Passive DNS Enumeration :
1. **DNSRecon** - It is a Python Script that is precompiled with Kali Linux. ```dnsrecon -d <domain_name> is the command used to perform Enumeration on the domain provided.```
2. DNSdumpster - It is a web-based application that performs DNS recon & research. The website is https://dnsdumpster.com/


# Reviewing Webserver Metafiles
Robots.txt is a file on the webserver that tell Search Engines not to include some directories present on the webserver onto the Search Engine, so that no crawler stores information about those routes or subdomains.

# Google Dorks

To limit all the results to a particular website, we need to use ```site:domain.com```
To check for keywords inside the URL, we need to use ```inurl:admin```
To get subdomains of a URL, we need to use ```site:*.domain.com```
To check for keywords in the title, we need to use ```inurl:admin```
We can also check for files for a current website, we need to use ```filetype:pdf```
Sometimes we find for the webservers with their "index of" site showing results, then we can use ```intitle:index of```
To know about the previous versions of the website, like how the website looked 5 months ago, we need to use ```cache:domain.com``` . For particularly this extraction, we can use https://wayback.archive.org
To know about the file with saved password with default name as auth_user_file.txt, we need to use ```inurl:auth_user_file.txt``` or ```inurl:passwd.txt```

# Web App Technology Fingerprinting
1. **BuiltWith** by garazy- Firefox add-on that helps to give information about the technologies being used by the web application.
2. **Wappalyzer** by Wappalyzer - Firefox add-on allows us to identify technologies on website.
3. **whatweb** - Kali Linux CLI Utility tool to find out information regarding technologies used by the websites.

# Web Application Firewalls Detection
https://github.com/EnableSecurity/wafw00f
Now, this tool comes prebuilt with Kali Linux. To check all the firewalls this tool can detect, we can check that using the command ```wafw00f -l```
How to use it to get information regarding the website : ```wafw00f <domain.com>```
To check for all possible WAF Instances, we need to use the command : ```waf00f domain.com -a```

# Copying a Website with HTTRack
The official website for HTTRack is : https://www.httrack.com/
To install that Kali Linux, we are going to use the command : ```sudo apt-get update -y && sudo apt-get install httrack```
To copy a website, we need to use the command : ```httrack <domain.com> -O <filename>```
![[Pasted image 20241023124916.png]]

Instead of using a single line command, we could actually use the CLI Tool, by using the command : ```httrack```
![[Pasted image 20241023125152.png]]

# Website Screenshots with EyeWitness
Eyewitness is a Kali Linux CLI tool that comes prebuilt with it. To install it, we can use the command : ```sudo apt-get install eyewitness``` 
1. To use this tool, we first need to create a text file with websites we want to take screenshot of.
2. Now, to use the tool, we need to enter the command : ```eyewitness --web -f domains.txt -d dir_name/```

# Passive Crawling & Spidering with Burp Suite & OWASP ZAP
![[Pasted image 20241109131835.png]]
![[Pasted image 20241109132012.png]]

#### For BurpSuite Crawler :
1. We need to setup the FoxyProxy to intercept the traffic towards BurpSuite
2. At the Dashboard Section of BurpSuite Community Edition, we get the **Live Passive Crawl from Proxy** Option.
3. Now, we jump into the New Live Task Option then it gives an option to create a sitemap of all the resources we visited while being on the website.
4. In the Professional BurpSuite, we can do the **Live Audit** and **Scan** which helps us to get more resources and URLs from the Website without passively checking the website.

#### For OWASP Zap :
1. We need to setup the FoxyProxy to intercept traffic towards ZAP, it uses the same Proxy as used for BurpSuite.
2. Now, to use ZAP, we just to need to reload the page, which could give us an error related to ZAP obviously.
3. Then go to Tools Section and Open up the Spider tool from there.
	![[Pasted image 20241109135557.png]]
4. In the Spider Section of ZAP, we could see two types of Processed Links i.e. One in the Red are External Hyperlinks and the One in Green are Internal Hyperlinks.
5. And we get a detailed sitemap, which many of the sites that are not visible on the frontend of the Website.

# Web Server Fingerprinting
To start with the scan we will use the famous tool called NMAP, using the command : ```nmap -sV -F <ip_address>```
When we get the information from the Scan regarding the Web Server with its version, we can use a tool like Searchsploit to get exploits for vulnerabilities present in the webserver.

Now to get more information about it, we will try to use a script, using the command : ```ls -a /usr/share/nmap/scripts | grep -e "server_name" ```
On the tested server we were using a http-enum script, hence use used the command : ```nmap -sV -p 80 --script=http-enum <ip_address>```
This script also enumerates some important directories.
 Now, after getting information regarding the potential vulnerabilities present on the webserver, we could directly to jump onto exploit them using Metasploit : 
```
1. metasploit
2. search auxiliary/scanner/http/http_version
3. use 0
4. show options (to check all the options that needs to be configured)
5. set RHOSTS <ip_address>
```

We could also use very famous option named **Curl** to get some information regarding the webserver.

Now to get more information regarding the directories present on the webserver, we could use **Dirb** , using the command : ```dirb <ip_address> /usr/share/metasploit-framework/data/wordlsits/directory.txt```

# DNS Zone Transfer
![[Pasted image 20241109164736.png]]
![[Pasted image 20241109164816.png]]

**DNS Interrogation**
	![[Pasted image 20241109164849.png]]

![[Pasted image 20241109164924.png]]

We can start the enumeration with **dnsdumpster.com** because it will provide us with the information regarding DNS Servers.
Now, to get similar information regarding DNS we could use a famous tool called **DNSRecon** , by using the command ```dnsrecon -d <website.com>```

Note : The hosts file for Kali Linux is present a the directory : `/etc/hosts` . Now to link a particular hostname to the local ip_address, we could simply add that up in this file like `<ipaddress> domain_name`

To get the information about the DNS Zone Transfer, we can run the command like : `dnsenum domain.com`

We can also use a DNS Lookup Utility named **dig** using the command : `dig axfr @nameserver domain.com `

We can also use a tool named **fierce** which scans and locates IP Spaces and hostnames which become a pre--cursor to nmap, unicornscan, nessus, nikto etc. To use it to get DNS Bruteforce, we can do that using the command : `fierce -dns domain.com`


# Subdomain Enumeration
### 1. Sublist3r - Passive Enumeration
Link - https://github.com/aboul3la/Sublist3r
To install we can just simply type in the command : `sudo apt-get install sublist3r`
To use it, just type in the command : `sublist3r -d domain.com`

### 2. Fierce 
The host list we are going to use to bruteforce the attack is from SecLists repository i.e. **fierece-hostlist.txt**
Now, to use a particular file and run Fierce, we will be using the command : `fierce --domain domain.com --subdomain-file fierce-hostlist.txt`

Basically after getting some IP or subdomains like that we can directly jump onto NMAP checking the services opened on them.

# Web Server Scanning with Nikto
To start scanning the webserver using Nikto, we can type in the command : `nikto -h http://ip_address`
And if we want to save the results in a htm file, we do that by using the command : `nikto -h http://ip_address -o filename.html -Format htm`

# File & Directory Brute-Force
Now, to run a Brute-force attack on Files & Directories, we use the command : `gobuster dir -u http://ip_address -w /usr/share/wordlists/common.txt`

Now if I don't want some particular error codes in a webserver and I need some particular extensions, then I can simply type in the command : `gobuster dir -u http://ip_address -w /usr/share/wordlists/dirb/common.txt -b 403,404 -x .php,.txt -r`


# Automated Web Recon with OWASP Amass (Practice the exact)
To install the tool, it comes with Kali Repo : `sudo apt-get install amass`
To use the tool for enumeration we can simply use the command :  `amass enum -d domain.com`
If we want to run Amass passively and taking output of the same, we can do that by using the command : `amss enum -d domain.com -passive -src -dir /path/`
If we want to do brute-forcing then we can use the flag `-brute` instead of `-passive`
For discovering targets for enumeration / reconnaissance, we can use the command `intel` instead of `enum`, hence the command becomes : `amass intel -active -whois -d domain.com -dir /path/`
 Now, to create a report out of this, we could do that using the option `viz` , the command becomes : `amass -viz -dir /path/ -d3`