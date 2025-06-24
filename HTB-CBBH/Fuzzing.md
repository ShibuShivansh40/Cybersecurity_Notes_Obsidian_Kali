`ffuf -w /root/SecLists/Discovery/Web-Content/directory-list-2.3-medium.txt -u http://94.237.55.96:59057/recursive_fuzz/FUZZ -t 2000 --recursion -ic`  : Recursive Approach to Fuzz the directories

`ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt -ic -v -u http://IP:PORT/FUZZ -e .html -recursion` : This is same as above


Parameter Fuzzing using Curl : `curl http://IP:PORT/get.php?x=1`


`curl -d "" http://IP:PORT/post.php` : The `-d` flag instructs `curl` to make a POST request with an empty body. 

>Invalid parameter value
>y: 
>The response tells us that the parameter `y` is expected but not provided.

`ffuf -u http://IP:PORT/post.php -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "y=FUZZ" -w /usr/share/seclists/Discovery/Web-Content/common.txt -mc 200 -v` : This is to fuzz the parameter.

# Virtual Hosts and Subdomains
![[Pasted image 20250318183802.png]]

`echo "IP inlanefreight.htb" | sudo tee -a /etc/hosts`

`gobuster vhost -u http://inlanefreight.htb:81 -w /usr/share/seclists/Discovery/Web-Content/common.txt --append-domain` : Using Gobuster for fuzzing vhosts.

`gobuster dns -d inlanefreight.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt` : For subdomain fuzzing


## Filtering Fuzzing Output
![[Pasted image 20250319144612.png]]
![[Screenshot 2025-03-19 144701.png]]

**Commands : **

`ffuf -u http://example.com/FUZZ -w wordlist.txt -mc 200 -fw 427 -ms >500` : Find directories with status code 200, based on the amount of words, and a response size greater than 500 bytes

`ffuf -u http://example.com/FUZZ -w wordlist.txt -fc 404,401,302` : Filter out responses with status codes 404, 401, and 302

`ffuf -u http://example.com/FUZZ.bak -w wordlist.txt -fs 0-10239 -ms 10240-102400` : Find backup files with the .bak extension and size between 10KB and 100KB

`ffuf -u http://example.com/FUZZ -w wordlist.txt -mt >500` : Discover endpoints that take longer than 500ms to respond

## Fuzzing the API

We will use a fuzzer that will use a wordlist in an attempt to discover these undocumented endpoints. Run the commands to pull, install the requirements, and run the fuzzer:

API Fuzzing

```shell-session
ShibuShivansh@htb[/htb]$ git clone https://github.com/PandaSt0rm/webfuzz_api.git
ShibuShivansh@htb[/htb]$ cd webfuzz_api
ShibuShivansh@htb[/htb]$ pip3 install -r requirements.txt
```

Then, run the fuzzer using the spawned target IP and PORT

API Fuzzing

```shell-session
ShibuShivansh@htb[/htb]$ python3 api_fuzzer.py http://IP:PORT

[-] Invalid endpoint: http://localhost:8000/~webmaster (Status code: 404)
[-] Invalid endpoint: http://localhost:8000/~www (Status code: 404)

Fuzzing completed.
Total requests: 4730
Failed requests: 0
Retries: 0
Status code counts:
404: 4727
200: 2
405: 1
Found valid endpoints:
- http://localhost:8000/cz...
- http://localhost:8000/docs
Unusual status codes:
405: http://localhost:8000/items
```

- The fuzzer identifies numerous invalid endpoints (returning `404 Not Found` errors).
- Two valid endpoints are discovered:
    - `/cz...`: This is an undocumented endpoint as it doesn't appear in the API documentation.
    - `/docs`: This is the documented Swagger UI endpoint.
- The `405 Method Not Allowed` response for `/items` suggests that an incorrect HTTP method was used to access this endpoint (e.g., trying a `GET` request instead of a `POST`).

We can explore the undocumented endpoint via curl and it will return a flag:

API Fuzzing

```shell-session
ShibuShivansh@htb[/htb]$ curl http://localhost:8000/cz...

{"flag":"<snip>"}
```
