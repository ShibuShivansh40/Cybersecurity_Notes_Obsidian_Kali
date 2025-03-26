### Structure of URL
![[Pasted image 20250326143249.png]]
### HTTP Flow
![[Pasted image 20250326143400.png]]

> **Note:** Our browsers usually first look up records in the local '`/etc/hosts`' file, and if the requested domain does not exist within it, then they would contact other DNS servers. We can use the '`/etc/hosts`' to manually add records to for DNS resolution, by adding the IP followed by the domain name.


### cURL
1. Command used to send a basic HTTP Request to URL : `curl inlanefreight.com`
2. Command used to download content of a particular file : `curl -O inlanefreight.com/index.html`
3. Command used to skip the SSL Certificate ch

### HTTPS Flow
![[Pasted image 20250326143830.png]]

> **Note:** Depending on the circumstances, an attacker may be able to perform an HTTP downgrade attack, which downgrades HTTPS communication to HTTP, making the data transferred in clear-text. This is done by setting up a Man-In-The-Middle (MITM) proxy to transfer all traffic through the attacker's host without the user's knowledge. However, most modern browsers, servers, and web applications protect against this attack.

