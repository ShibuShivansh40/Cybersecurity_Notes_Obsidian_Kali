For Recon : 
[ ] - Use this command under a folder named as Target
	```assetfinder --subs-only target.com >> recon.txt  
	subfinder -d target.com -silent >> recon.txt  
	amass enum -passive -d target.com >> recon.txt  
	sort -u recon.txt > final-subs.txt
	cat final-subs.txt | httpx -status-code -title -tech-detect -silent > live-subs.txt```
[ ] - Check for `robots.txt` and `sitemap.xml` for subdomains and directories
[ ] - Checking for Secrets in JS FIles
	1. Download all the JS Files present.
	2. Use the command to grep the secrets, keys and tokens : 		```
		cat js_files.txt | while read url; do curl -s $url >> all_javascript_dump.txt; done  
		grep -iE "apikey|token|secret|authorization|bearer" all_javascript_dump.txt
		```
[ ] - Bruteforce checking all JS Files : `ffuf -w common.txt -u https://target.com/assets/js/FUZZ`
[ ] - Always check User Agent for for Logs, it may give RFi
[ ] - Checking for 403 Forbidden : 
	[ ] - **Adding headers** (like `X-Forwarded-For`, `X-Originating-IP`)
	[ ] - **Trying HTTP methods** (`GET`, `POST`, `HEAD`, `OPTIONS`)
	[ ] - **Using URL encoding tricks** (`%2e`, `%2f`, etc.)
	[ ] - **Appending a dot (**`**.**`**) or a slash (**`**/**`**) at the end**
	[ ] - **Spoofing the Referer header** (`Referer: example.com/allowed-page`)

[ ] - Check for the parameter named `redirect` that is used to redirect the site to the internal sites and then try to pollute it like : `https://app.target.com/login?redirect=dashboard&redirect=https://evil.com`
[ ] - Required payloads to be tried once : 
	```curl https://target.com/config/settings_dev.json
	curl https://target.com/.env
	curl https://target.com/.git/config```
[ ] - 