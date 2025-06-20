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