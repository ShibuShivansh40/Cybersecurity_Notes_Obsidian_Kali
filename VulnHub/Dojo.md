## Network Enumeration

```
┌──(root㉿kali)-[~]
└─# sudo netdiscover -r 10.0.2.1/24

 Currently scanning: Finished!   |   Screen View: Unique Hosts                                                                                                                                                                                                                                                                                                                          
 3 Captured ARP Req/Rep packets, from 3 hosts.   Total size: 184                                                                                                                            
 _____________________________________________________________________________   IP            At MAC Address     Count     Len  MAC Vendor / Hostname       ----------------------------------------------------------------------------- 10.0.2.3        08:00:27:ba:99:14      1      60  PCS Systemtechnik GmbH                                                                                                                    10.0.2.15       08:00:27:ee:1b:3a      1      60  PCS Systemtechnik GmbH                                                                                                                   
 10.0.2.1        52:55:0a:00:02:01      1      64  Unknown vendor

┌──(root㉿kali)-[~]
└─# nmap -p- -sS -sV -A 10.0.2.15
Starting Nmap 7.95 ( https://nmap.org ) at 2025-12-02 06:09 EST
Nmap scan report for 10.0.2.15
Host is up (0.00071s latency).
Not shown: 65532 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
80/tcp   open  http        Apache httpd 2.2.22 ((Ubuntu))
|_http-server-header: Apache/2.2.22 (Ubuntu)
|_http-title: 403 Forbidden
5001/tcp open  java-object Java Object Serialization
8080/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
| http-methods: 
|_  Potentially risky methods: PUT DELETE
|_http-title: Apache Tomcat
|_http-server-header: Apache-Coyote/1.1
|_http-open-proxy: Proxy might be redirecting requests
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port5001-TCP:V=7.95%I=7%D=12/2%Time=692EC8E0%P=x86_64-pc-linux-gnu%r(NU
SF:LL,4,"\xac\xed\0\x05");
MAC Address: 08:00:27:EE:1B:3A (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Linux 2.6.X|3.X
OS CPE: cpe:/o:linux:linux_kernel:2.6 cpe:/o:linux:linux_kernel:3
OS details: Linux 2.6.32 - 3.5
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   0.71 ms 10.0.2.15

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 39.88 seconds

```