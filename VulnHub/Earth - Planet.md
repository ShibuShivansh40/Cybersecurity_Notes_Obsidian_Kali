```
>> sudo netdiscover -r 10.0.2.1/24
 Currently scanning: Finished!   |   Screen View: Unique Hosts                                                                                                                                                   
                                                                                                                                                                                                                 
 3 Captured ARP Req/Rep packets, from 3 hosts.   Total size: 184                                                                                                                                                 
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 10.0.2.3        52:55:0a:00:02:03      1      64  Unknown vendor                                                                                                                                                
 10.0.2.3        08:00:27:cd:6f:f4      1      60  PCS Systemtechnik GmbH                                                                                                                                        
 10.0.2.12       08:00:27:79:18:f3      1      60  PCS Systemtechnik GmbH                                                                                                                                        
┌──(root㉿kali)-[~]
└─# nmap -p- -sS -sV -A 10.0.2.12
Starting Nmap 7.95 ( https://nmap.org ) at 2025-12-01 01:30 EST
Nmap scan report for 10.0.2.12
Host is up (0.00068s latency).
Not shown: 65379 filtered tcp ports (no-response), 153 filtered tcp ports (admin-prohibited)
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 8.6 (protocol 2.0)
| ssh-hostkey: 
|   256 5b:2c:3f:dc:8b:76:e9:21:7b:d0:56:24:df:be:e9:a8 (ECDSA)
|_  256 b0:3c:72:3b:72:21:26:ce:3a:84:e8:41:ec:c8:f8:41 (ED25519)
80/tcp  open  http     Apache httpd 2.4.51 ((Fedora) OpenSSL/1.1.1l mod_wsgi/4.7.1 Python/3.9)
|_http-server-header: Apache/2.4.51 (Fedora) OpenSSL/1.1.1l mod_wsgi/4.7.1 Python/3.9
|_http-title: Bad Request (400)
443/tcp open  ssl/http Apache httpd 2.4.51 ((Fedora) OpenSSL/1.1.1l mod_wsgi/4.7.1 Python/3.9)
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.51 (Fedora) OpenSSL/1.1.1l mod_wsgi/4.7.1 Python/3.9
|_http-title: Test Page for the HTTP Server on Fedora
|_ssl-date: TLS randomness does not represent time
| tls-alpn: 
|_  http/1.1
| ssl-cert: Subject: commonName=earth.local/stateOrProvinceName=Space
| Subject Alternative Name: DNS:earth.local, DNS:terratest.earth.local
| Not valid before: 2021-10-12T23:26:31
|_Not valid after:  2031-10-10T23:26:31
MAC Address: 08:00:27:79:18:F3 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: Linux 4.15 - 5.19 (97%), Linux 5.0 - 5.14 (97%), OpenWrt 21.02 (Linux 5.4) (97%), Linux 4.19 (95%), Linux 6.0 (94%), MikroTik RouterOS 7.2 - 7.5 (Linux 5.6.3) (94%), Linux 2.6.32 (91%), Linux 2.6.32 - 3.13 (91%), Linux 3.10 - 4.11 (91%), Linux 3.2 - 4.14 (91%)                                                                                                                                                                                             
No exact OS matches for host (test conditions non-ideal).                                                                                                                                                                                   
Network Distance: 1 hop                                             
TRACEROUTE                                        
HOP RTT     ADDRESS                                               
1   0.68 ms 10.0.2.12                                                                                                                                     
OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .                                                                                                                                       
Nmap done: 1 IP address (1 host up) scanned in 165.87 seconds     

```

NMAP got nothing directly attacking the VM. So I'm going for Password bruteforce for root.

