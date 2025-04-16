Playlist Link to be followed : https://www.youtube.com/playlist?list=PLbyncTkpno5HqX1h2MnV6Qt4wvTb8Mpol


# How to use FFuF ? 
![[Pasted image 20250224180658.png]]
![[Screenshot 2025-02-24 180752.png]]![[Pasted image 20250224180949.png]]

Basic Usage : `ffuf -w wordlist.txt -u http://ip:port/api/FUZZ/6 -o output.txt -replay-proxy http://proxy_ip:port` - This allows us to directly send all the Good Traffic to Burp by providing it with Burp's Proxy.
We can add cookies by adding up `-b "cookie"` to the above command.
![[Pasted image 20250224181501.png]]
We can also FUZZ the headers according to our will, using the command : `ffuf -w wordlist.txt -u http://127.0.0.1:8000/api/users/6 -o output.txt -replay-proxy http://127.0.0.1:8080 -H "User-Agent: FUZZ"`

We can add the number of threads by providing it the flag : `-t 10`
We can add the seconds as delay between requests with `-p 3`

![[Pasted image 20250224182135.png]]
![[Pasted image 20250224182205.png]]
![[Pasted image 20250224182226.png]]
![[Pasted image 20250224182307.png]]
![[Pasted image 20250224182406.png]]
`ffuf -w worlist.txt:FUZZ -w numbers:ME -u http:127.0.0.1:8000/api/FUZZ?ME -o output.txt -replay-proxy http:127.0.0.1:8080 -f "Not Found"` - This would filter out the output using the filter regex flag.

![[Pasted image 20250224182723.png]]
![[Pasted image 20250224182804.png]]
![[Pasted image 20250224182834.png]]
![[Pasted image 20250224182945.png]]
