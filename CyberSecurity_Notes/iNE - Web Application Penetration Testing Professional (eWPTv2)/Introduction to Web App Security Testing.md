## **Web Application Security Testing Types**
- **Vulnerability Scanning** : Using automated tools to scan the web application for known vulnerabilities, such as SQL Injections, Cross Site Scripting, Insecure Configurations and outdated software versions.
- **Penetration Testing** : It is a subset of WebApp Security Testing. Simulating real-world attacks to assess the application's defenses and identify potential security weaknesses. This involves ethical hacking to gain insights into how an attacker might exploit vulnerabilities.
- **Code Review and Static Analysis** : Manual examination of the application's source code to identify coding flaws, security misconfigurations and potential security risks.
- **Authentication and Authorization Testing** : Evaluating the effectiveness of authentication mechanisms and access control features to ensure that only authorized users have appropriate access levels.
- **Input Validation and Output Encoding Testing** : Assessing how the application handles user inputs to prevent common security vulnerabilities like XSS and SQL Injection.
- **Session Management Testing** : Verifying how the application manages user sessions and related tokens to prevent session-related attacks.
- **API Security Testing** : Assessing the security of APIs used by the web application for data exchange and integration with other systems.

## **Web Application Penetration Testing**
- Web application pentesting is a subset of web application security testing that specifically involves attempting to exploit identified vulnerabilities.
- It is a simulated attack on the web application conducted by skilled security professionals known as pentesters, bug bounty hunters or ethical hackers.
- The process involves  a systematic and controlled approach to assess the application's security by attempting to exploit known vulnerabilities.
![[Pasted image 20241015123110.png]]

## **Common Web Application Threats & Risks**
 - **Threat**
	 - A threat refers to any potential source of harm or adverse event that may exploit a vulnerability in a system or organization's security measures.
	 - Threats can be human - made, such as cybercriminals, hackers or insiders with malicious intent, or they can be natural, such as floods, earthquakes or power outages.
	 - In context of cybersecurity, threats can include various types of attacks like malware infections, phishing attempts, denial-of-service attacks, and data breachers.

- **Risk**
	- Risk is a potential for a loss or harm resulting from a threat exploiting a vulnerability in a system or organization.
	- It is a combination of the likelihood or probability of a threat occurrence and the impact or severity of the resulting adverse event.
	- Risk is often measured in terms of the likelihood of an incident happening and the potential magnitude of its impact.

![[Pasted image 20241016011238.png]]
## **Web Application Architecture & Components**
![[Pasted image 20241015151412.png]]

![[Pasted image 20241015153034.png]]![[Pasted image 20241016224631.png]]
![[Pasted image 20241016224824.png]]
![[Pasted image 20241016225526.png]]![[Pasted image 20241016225634.png]]
![[Pasted image 20241016225645.png]]![[Pasted image 20241016225939.png]]

### Web Application Technologies
![[Pasted image 20241016232328.png]]

**Client Side Technologies**
![[Pasted image 20241016230338.png]]

**Web Server Technologies**
![[Pasted image 20241016230632.png]]
![[Pasted image 20241016230814.png]]


**Data Interchange**
![[Pasted image 20241016231504.png]]

**Data Interchange Technologies**
![[Pasted image 20241016231626.png]]

**Data Interchange Protocol**
![[Pasted image 20241016231820.png]]
![[Pasted image 20241016231912.png]]

**Security Technologies**
![[Pasted image 20241016231929.png]]

**External Technologies**
![[Pasted image 20241016232206.png]]

**How are Web Pages Rendered ?**
![[Pasted image 20241016232559.png]]

**How Browser Parse Responses ?**
![[Pasted image 20241016232832.png]]

# HTTP Protocol Fundamentals
**HTTP Protocol**
![[Pasted image 20241017123401.png]]

**HTTP Request Components**
![[Pasted image 20241019000609.png]]
![[Pasted image 20241019000715.png]]
![[Pasted image 20241019001252.png]]
 **HTTP Request Example**
 ![[Pasted image 20241019001516.png]]
 ![[Pasted image 20241019001953.png]]

 **HTTP Request Methods**
 ![[Pasted image 20241019002018.png]]
 
 **HTTP Request Methods**
 ![[Pasted image 20241019002151.png]]

 **HTTP Request URL/Path**
![[Pasted image 20241019003024.png]]

**HTTP Request Host Header**
![[Pasted image 20241019003534.png]]

**HTTP Request User-Agent Header**
![[Pasted image 20241019004231.png]]

**HTTP Request Accept Header**
![[Pasted image 20241019004314.png]]

**HTTP Request Accept-Encoding Header**
![[Pasted image 20241019004613.png]]

**HTTP Request Connection Header**
![[Pasted image 20241019004945.png]]

 **HTTP Response Components**
 ![[Pasted image 20241019005635.png]]
**HTTP Request Response**
![[Pasted image 20241019010646.png]]
![[Pasted image 20241019010829.png]]

**HTTP Response Status-Line**
![[Pasted image 20241019010913.png]]
![[Pasted image 20241019011039.png]]

**HTTP Response Date Header**
![[Pasted image 20241019143047.png]]

**HTTP Response Cache Control Header**
![[Pasted image 20241019143207.png]]
![[Pasted image 20241019143220.png]]

**HTTP Response Content Type Header**
![[Pasted image 20241019145623.png]]

**HTTP Response Content Encoding Header**
![[Pasted image 20241019145738.png]]

**HTTP Response Server Header**
![[Pasted image 20241019145821.png]]

```
Correct way to load Wireshark on Kali CLI : wireshark -i <interface_name>
```

```
To check for all the connection made, use the command : netstat -antp
```

Curl is a very useful tool with respect to Web Penetration. It helps in getting responses from the web server using CLI.
```
The command used to send a HTTP Request to an IP Address with the verbose flag -v is : curl -v <ip_address>
```
![[Pasted image 20241019152742.png]]
How curl executed the current command : 
- It tried to establish a TCP Connection with the webserver
- Then it sends an actual HTTP Request to the webserver, to confirm that we didn't use  web browser in the whole we can see that, it is written curl in the User-Agent Flag.
- Then it prints us the Response of the web server.

It shows us that X-Powered-By Flag is set to PHP, that means the backend programming language for the web server is PHP in this case. And it also gives a brief about the underlying Operating System, the web server is working on.

```
The command to send the HEAD Request Methods to the Web Server, we use the command : curl -v -I  <ip_address>
```

![[Pasted image 20241019155410.png]]

```
To know about the different Request Methods accepted by the Web Server, we ues the command : curl -v -X OPTIONS <ip_address>
```

![[Pasted image 20241019155611.png]]

```
To find all the directories present in the web server we can use the tool named as DIRB, using the command : dirb <ip_address/url>
```
![[Pasted image 20241019161103.png]]

In the burp suite, if we wanna know what kind of Request Methods are allowed, we can change the header to OPTIONS:
![[Pasted image 20241019161348.png]]

**DAV** : It is a protocol that allows users to send file, copy, move or edit files of webserver typically documentation. We can use this as a vulnerability to upload and edit files in the web server.

```
To check for scripts and stuff, example searching for a PHP Webshell, we can navigate in Kali, using the command : ls -al /usr/share/webshells/php/
```

```
To send such a script to the web server directory using curl, use the commmand : curl <ip_address>/directory --upload-file /file_path/
```

### HTTPS
 ![[Pasted image 20241019162842.png]]
 ![[Pasted image 20241019163002.png]]![[Pasted image 20241019163212.png]]
  **HTTPS Advantage**
  ![[Pasted image 20241019163405.png]]
**HTTPS Security Considerations**
![[Pasted image 20241019163504.png]]

# Web App Pentesting 
**Importance of Web App Pentesting Methodologies**
![[Pasted image 20241019231605.png]]
![[Pasted image 20241019231845.png]]
 ![[Pasted image 20241019231957.png]]

**We App Pentesting Methodologies**
![[Pasted image 20241019221701.png]]
![[Pasted image 20241019232320.png]]
 ![[Pasted image 20241019232948.png]]

**Penetration Testing Methodologies**
![[Pasted image 20241019233231.png]]

- **Penetration Testing Execution Standard**
	![[Pasted image 20241019233317.png]]

- **OWASP Web Security Testing Guide (WSTG)**
	![[Pasted image 20241019233407.png]]

### **OWASP TOP 10**
![[Pasted image 20241019233603.png]]
**OWASP Top 10 Releases**
![[Pasted image 20241019233748.png]]
![[Pasted image 20241019233922.png]]

## **OWASP Web Security Testing Guide (WSTG)**
 ![[Pasted image 20241020145834.png]]
 ![[Pasted image 20241020145901.png]]
The Repository for the WSTG :  https://github.com/owasp/wstg
It contains an Excel sheet with the checklist.

### **Pre-Engagement Phase**
![[Pasted image 20241020223530.png]]
![[Pasted image 20241020223555.png]]
**Steps : **
![[Pasted image 20241020223737.png]]
![[Pasted image 20241020223906.png]]
![[Pasted image 20241020223945.png]]
![[Pasted image 20241020224102.png]]

### **Documenting & Communicating Findings **
**Web App Pentesting Report**\
![[Pasted image 20241020224316.png]]
**Writing the Report**
![[Pasted image 20241020224510.png]]
**Documenting your Findings**
![[Pasted image 20241020224710.png]]
![[Pasted image 20241020230209.png]]
**Web App Pentest Report Structure**
![[Pasted image 20241020230437.png]]
![[Pasted image 20241020230554.png]]
![[Pasted image 20241020230715.png]]
![[Pasted image 20241020230745.png]]
![[Pasted image 20241020230837.png]]

Website for Report Making and Report Reading : www.pentestreports.com/
