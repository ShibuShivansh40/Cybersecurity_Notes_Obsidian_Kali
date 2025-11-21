```

>> sudo netdiscover -r 10.0.2.1/24
 Currently scanning: Finished!   |   Screen View: Unique Hosts                                                                      
                                                                                                                                    
 6 Captured ARP Req/Rep packets, from 3 hosts.   Total size: 364                                                                    
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 10.233.56.106   08:00:27:bd:ad:d1      4     240  PCS Systemtechnik GmbH                                                           
 10.0.2.3        52:55:0a:00:02:03      1      64  Unknown vendor                                                                   
 10.0.2.3        08:00:27:fe:68:8c      1      60  PCS Systemtechnik GmbH       

──(root㉿kali)-[/home/kali]
└─# nmap -A -T4 -sV -sS 10.233.56.106 -p-
Starting Nmap 7.95 ( https://nmap.org ) at 2025-11-20 01:47 EST
Nmap scan report for 10.233.56.106
Host is up (0.015s latency).
All 65535 scanned ports on 10.233.56.106 are in ignored states.
Not shown: 62105 filtered tcp ports (net-unreach), 3430 filtered tcp ports (no-response)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: 3Com 4500G switch (92%), H3C Comware 5.20 (92%), Huawei VRP 8.100 (92%), Microsoft Windows Server 2003 SP1 (92%), Oracle Virtualbox Slirp NAT bridge (92%), QEMU user mode network gateway (92%), AXIS 2100 Network Camera (92%), D-Link DP-300U, DP-G310, or Hamlet HPS01UU print server (92%), HP Tru64 UNIX 5.1A (92%), Sanyo PLC-XU88 digital video projector (92%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop

TRACEROUTE (using port 80/tcp)
HOP RTT      ADDRESS
1   19.73 ms 10.233.56.106

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 52.65 seconds


```

Learnt a Lesson, machine comes in Bridged Adapter state, use it in that state only.

```
┌──(root㉿kali)-[/home/kali]
└─# nmap -p- -sS -sV -A 10.233.56.162
Starting Nmap 7.95 ( https://nmap.org ) at 2025-11-21 01:16 EST
Nmap scan report for 10.233.56.162
Host is up (0.00025s latency).
Not shown: 65530 closed tcp ports (reset)
PORT      STATE SERVICE     VERSION
80/tcp    open  http        Apache httpd 2.4.51 ((Debian))
|_http-title: Apache2 Debian Default Page: It works
|_http-server-header: Apache/2.4.51 (Debian)
139/tcp   open  netbios-ssn Samba smbd 4
445/tcp   open  netbios-ssn Samba smbd 4
10000/tcp open  http        MiniServ 1.981 (Webmin httpd)
|_http-title: 200 &mdash; Document follows
20000/tcp open  http        MiniServ 1.830 (Webmin httpd)
|_http-title: 200 &mdash; Document follows
|_http-server-header: MiniServ/1.830
MAC Address: 08:00:27:42:54:DD (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Linux 4.X|5.X
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5
OS details: Linux 4.15 - 5.19, OpenWrt 21.02 (Linux 5.4)
Network Distance: 1 hop

Host script results:
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2025-11-21T06:17:11
|_  start_date: N/A
|_nbstat: NetBIOS name: BREAKOUT, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)

TRACEROUTE
HOP RTT     ADDRESS
1   0.25 ms 10.233.56.162

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 44.42 seconds
    
```

![[Screenshot From 2025-11-21 12-09-42.png]]

![[Pasted image 20251121121002.png]]


```
                                                                             
┌──(kali㉿kali)-[~]
└─$ searchsploit "Samba smdb 4"       
Exploits: No Results
Shellcodes: No Results
                                                                             
┌──(kali㉿kali)-[~]
└─$ searchsploit "MiniServ 1.981"
Exploits: No Results
Shellcodes: No Results
                                                                             
┌──(kali㉿kali)-[~]
└─$ searchsploit "MiniServ 1.830"
Exploits: No Results
Shellcodes: No Results
                                                                             
┌──(kali㉿kali)-[~]
└─$ searchsploit webmin 1.984    
------------------------------------------- ---------------------------------
 Exploit Title                             |  Path
------------------------------------------- ---------------------------------
Webmin 1.984 - Remote Code Execution (Auth | linux/webapps/50809.py
------------------------------------------- ---------------------------------
Shellcodes: No Results
                                               
```

