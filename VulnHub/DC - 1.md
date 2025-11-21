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
