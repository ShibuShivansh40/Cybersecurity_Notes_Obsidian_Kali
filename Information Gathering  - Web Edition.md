![[Pasted image 20250328130335.png]]

## Active Reconnaissance
![[Screenshot From 2025-03-28 13-04-30.png]]
![[Pasted image 20250328130504.png]]

## Passive Reconnaissance
![[Pasted image 20250328130654.png]]

## WHOIS
WHOIS is a widely used query and response protocol designed to access databases that store information about registered internet resources. Primarily associated with domain names, WHOIS can also provide details about IP address blocks and autonomous systems. Think of it as a giant phonebook for the internet, letting you look up who owns or is responsible for various online assets.

```shell-session
ShibuShivansh@htb[/htb]$ whois inlanefreight.com

[...]
Domain Name: inlanefreight.com
Registry Domain ID: 2420436757_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.registrar.amazon
Registrar URL: https://registrar.amazon.com
Updated Date: 2023-07-03T01:11:15Z
Creation Date: 2019-08-05T22:43:09Z
[...]
```

Each WHOIS record typically contains the following information:

- `Domain Name`: The domain name itself (e.g., example.com)
- `Registrar`: The company where the domain was registered (e.g., GoDaddy, Namecheap)
- `Registrant Contact`: The person or organization that registered the domain.
- `Administrative Contact`: The person responsible for managing the domain.
- `Technical Contact`: The person handling technical issues related to the domain.
- `Creation and Expiration Dates`: When the domain was registered and when it's set to expire.
- `Name Servers`: Servers that translate the domain name into an IP address.

### DNS Tools
![[Pasted image 20250328131603.png]]

## Dig Commands
![[Pasted image 20250328131731.png]]

## Subdomain Enumeration
### 1. Active Subdomain Enumeration

This involves directly interacting with the target domain's DNS servers to uncover subdomains. One method is attempting a `DNS zone transfer`, where a misconfigured server might inadvertently leak a complete list of subdomains. However, due to tightened security measures, this is rarely successful.

A more common active technique is `brute-force enumeration`, which involves systematically testing a list of potential subdomain names against the target domain. Tools like `dnsenum`, `ffuf`, and `gobuster` can automate this process, using wordlists of common subdomain names or custom-generated lists based on specific patterns.

### 2. Passive Subdomain Enumeration

This relies on external sources of information to discover subdomains without directly querying the target's DNS servers. One valuable resource is `Certificate Transparency (CT) logs`, public repositories of SSL/TLS certificates. These certificates often include a list of associated subdomains in their Subject Alternative Name (SAN) field, providing a treasure trove of potential targets.

Another passive approach involves utilising `search engines` like Google or DuckDuckGo. By employing specialised search operators (e.g., `site:`), you can filter results to show only subdomains related to the target domain.

Additionally, various online databases and tools aggregate DNS data from multiple sources, allowing you to search for subdomains without directly interacting with the target.

Each of these methods has its strengths and weaknesses. Active enumeration offers more control and potential for comprehensive discovery but can be more detectable. Passive enumeration is stealthier but might not uncover all existing subdomains. Combining both approaches provides a more thorough and effective subdomain enumeration strategy.

Command used for Subdomain Enumeration, using DNSEnum :
```bash
dnsenum --enum inlanefreight.com -f /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -r
```

## DNS Zone Transfer
![[Pasted image 20250402105222.png]]

Command to request a Zone Transfer : `dig axfr @nsztm1.digi.ninja zonetransfer.me

## Vhost Fuzzing
![[Pasted image 20250402123511.png]]

Gobuster command to brute-force vhosts : `gobuster vhost -u http://<target_IP_address> -w <wordlist_file> --append-domain`

## CT Logs
![[Pasted image 20250402131425.png]]

## crt.sh Lookup
 Command to find a particular string of subdomain present on a website using cURL : `curl -s "https://crt.sh/?q=facebook.com&output=json" | jq -r '.[]  | select(.name_value | contains("dev")) | .name_value' | sort -u`
