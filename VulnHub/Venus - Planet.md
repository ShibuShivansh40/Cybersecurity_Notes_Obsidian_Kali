```
 Currently scanning: Finished!   |   Screen View: Unique Hosts                                                                                                                              
                                                                                                                                                                                            
 3 Captured ARP Req/Rep packets, from 2 hosts.   Total size: 180                                                                                                                            
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 10.0.2.3        08:00:27:ba:99:14      2     120  PCS Systemtechnik GmbH                                                                                                                   
 10.0.2.15       08:00:27:18:54:5e      1      60  PCS Systemtechnik GmbH             
 
```

## NMAP : 
```
┌──(root㉿kali)-[~]
└─# nmap -p- -sS -sV -A 10.0.2.15
Starting Nmap 7.95 ( https://nmap.org ) at 2025-12-02 06:30 EST
Nmap scan report for 10.0.2.15
Host is up (0.00064s latency).
Not shown: 65327 filtered tcp ports (no-response), 206 filtered tcp ports (admin-prohibited)
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.5 (protocol 2.0)
| ssh-hostkey: 
|   256 b0:3e:1c:68:4a:31:32:77:53:e3:10:89:d6:29:78:50 (ECDSA)
|_  256 fd:b4:20:d0:d8:da:02:67:a4:a5:48:f3:46:e2:b9:0f (ED25519)
8080/tcp open  http    WSGIServer 0.2 (Python 3.9.5)
|_http-title: Venus Monitoring Login
MAC Address: 08:00:27:18:54:5E (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose|router|storage-misc
Running (JUST GUESSING): Linux 4.X|5.X|6.X|2.6.X|3.X (97%), MikroTik RouterOS 7.X (97%), Synology DiskStation Manager 5.X (89%)
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5 cpe:/o:mikrotik:routeros:7 cpe:/o:linux:linux_kernel:5.6.3 cpe:/o:linux:linux_kernel:6.0 cpe:/o:linux:linux_kernel:2.6.32 cpe:/o:linux:linux_kernel:3 cpe:/a:synology:diskstation_manager:5.2
Aggressive OS guesses: Linux 4.15 - 5.19 (97%), Linux 4.19 (97%), Linux 5.0 - 5.14 (97%), OpenWrt 21.02 (Linux 5.4) (97%), MikroTik RouterOS 7.2 - 7.5 (Linux 5.6.3) (97%), Linux 6.0 (95%), Linux 5.4 - 5.10 (91%), Linux 2.6.32 (91%), Linux 2.6.32 - 3.13 (91%), Linux 3.10 (91%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   0.64 ms 10.0.2.15

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 217.08 seconds
```

After a lot of tries, I reached in here.
![[Pasted image 20251203111412.png]]
Then after logging into this I found the request packet at Burp to look like this with the cookies authorization : 
![[Pasted image 20251203111941.png]]


```
┌──(kali㉿kali)-[~]
└─$ echo "Z3Vlc3Q6dGhyZmc=" |base64 -d                                         
guest:thrfg   
```

This was the actual cookie present where `guest` is the login id but `thrfg` is something unique. And when I looked into it basically `thrfg` is the ROT13 Encryption of the username itself.

So, I'll try to put the cookies now as `admin:rot13<admin>`

## User Enumeration
![[Pasted image 20251203131221.png]]

