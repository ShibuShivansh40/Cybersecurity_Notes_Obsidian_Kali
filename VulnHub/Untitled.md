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
└─# nmap -p- 10.233.56.60     
Starting Nmap 7.95 ( https://nmap.org ) at 2025-11-20 02:21 EST
Nmap scan report for 10.233.56.60
Host is up (0.0044s latency).
Not shown: 65533 closed tcp ports (reset)
PORT      STATE SERVICE
53/tcp    open  domain
44497/tcp open  unknown
MAC Address: BE:88:08:70:F5:61 (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 10.79 seconds
                                                                                                                                                                      
┌──(root㉿kali)-[/home/kali]
└─# nmap -A -T4 -sV -sS 10.233.56.60 -p-
Starting Nmap 7.95 ( https://nmap.org ) at 2025-11-20 02:21 EST
Nmap scan report for 10.233.56.60
Host is up (0.0061s latency).
Not shown: 65533 closed tcp ports (reset)
PORT      STATE SERVICE    VERSION
53/tcp    open  domain     dnsmasq 2.51
| dns-nsid: 
|_  bind.version: dnsmasq-2.51
44497/tcp open  tcpwrapped
MAC Address: BE:88:08:70:F5:61 (Unknown)
Device type: phone
Running: Google Android 10.X, Linux 4.X
OS CPE: cpe:/o:google:android:10 cpe:/o:linux:linux_kernel:4
OS details: Android 9 - 10 (Linux 4.9 - 4.14)
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   6.07 ms 10.233.56.60

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 26.69 seconds


┌──(root㉿kali)-[/home/kali]
└─# searchsploit "dnsmasq 2.51"
------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------
 Exploit Title                                                                                                                      |  Path
------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------
Dnsmasq < 2.78 - 2-byte Heap Overflow                                                                                               | multiple/dos/42941.py
Dnsmasq < 2.78 - Heap Overflow                                                                                                      | multiple/dos/42942.py
Dnsmasq < 2.78 - Information Leak                                                                                                   | multiple/dos/42944.py
Dnsmasq < 2.78 - Integer Underflow                                                                                                  | multiple/dos/42946.py
Dnsmasq < 2.78 - Lack of free() Denial of Service                                                                                   | multiple/dos/42945.py
Dnsmasq < 2.78 - Stack Overflow                                                                                                     | multiple/dos/42943.py
------------------------------------------------------------------------------------------------------------------------------------ ---------------------------------
Shellcodes: No Results
                                                          
```


