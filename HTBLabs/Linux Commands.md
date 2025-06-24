## SMB
1. `smbclient \\\\10.129.235.5\\WorkShares`
	![[Pasted image 20250624160541.png]]
2. `smb: \> get flag.txt` - To download the flag
	![[Pasted image 20250624160837.png]]
3. `smb: \> get flag.txt -` - To download the flag and also print the content 
4. `smb: \> help` - To know about the commands we can use
	![[Pasted image 20250624160909.png]]
5. `smb: \> cd dir` - To change the directory


## NMAP
1. `nmap -T5 -sV 10.129.235.9` - To perform Service Enumeration 
2. ` nmap -sV 10.129.27.64 -p- -T5` - To perform Service Enumeration on all ports available at a quick pace.

## Redis-CLI
1. `redis-cli -h 1.129.235.5` - To start interacting with the server
2. 
3. 