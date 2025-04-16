### 11Feb25

1.  **Lab :** Reflected XSS into HTML context with nothing encoded
	**Solution :** Just added a simple XSS Payload in the search box and it showed me a Reflect XSS. Payload Added was `<script>alert(1)</script>` 

2. ***Lab* :** Stored XSS into HTML context with nothing encoded
	***Solution*** : As we know it's a stored XSS Vulnerability, hence we could only find it where could add the stuff to the website which can be either comments or posts. So, I visited the comment section and then added the normal script `<script><alert(1)</script>`. And on simply reloading the page we got to see the alert.

3. ***Lab :*** DOM XSS in `document.write` sink using source `location.search`
	***Solution :*** Here, when I'm trying to input some value then it converting that into some encoding. So I was looking into the wrong variables and files. I first need to send some data and look out for where the payload is getting injected actually. Once found, then we could create our own payload and get alerts. Here, I was required to put a payload like `"><script>alert(1)</script>` as the data was getting stored into an `<img>` tag.

4. ***Lab:*** DOM XSS in document.write sink using source location.search inside a select element
	***Solution :***  I first try to add the payload in the `procductId` parameter but then I found out that I could also add a new parameter named `storeId` and there I changed the URL to `product?productId=1&storeId="><script>alert(1)</script>`

5. ***Lab :***  DOM XSS in jQuery anchor href attribute sink using location.search source
	***Solution :*** Adding `javascript:alret(document.cookie)` instead of `/post` would solve the lab. But due to some issues it's not done yet.

6. ***Lab :*** DOM XSS in jQuery selector sink using a hashchange event
	***Solution :***  We were required to add a payload for iframe in the exploit-server and deliver that to the victim. The payload used was : `<iframe src="https://0aa100f904d0d2348f9b941b006800a1.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>`

7. ***Lab :*** DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded
	***Solution :*** Add a simple payload into the Lab's Search Box which takes advantage of `ng-app` vulnerabilities. The payload was : `{{$on.constructor('alert(1)')()}}` 

### 19Feb25

1. ***Lab*** : Stored XSS into HTML context with nothing encoded
	***Solution :*** As it contains stored, hence comments act as the stored data on every reload on the route, hence add a basic payload like `<script>alert(1)</script>`

2. 