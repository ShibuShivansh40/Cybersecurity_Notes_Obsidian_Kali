### Types of XSS
![[Pasted image 20250403133356.png]]

## Stored XSS
It is the critical type of XSS, as payload gets stored inside the Backed Database and whenever a user tries to visit the website, it fetches the payload and executes it for the user.

XSS Testing Payload :  
- `<script>alret(windows.origin)</script>`
- `<script>print()</script>`

## Non-Persistent XSS
But if the XSS vulnerability is Non-Persistent, how would we target victims with it?

This depends on which HTTP request is used to send our input to the server. We can check this through the Firefox `Developer Tools` by clicking [`CTRL+Shift+I`] and selecting the `Network` tab. Then, we can put our `test` payload again and click `Add` to send it:
As we can see, the first row shows that our request was a `GET` request. `GET` request sends their parameters and data as part of the URL. So, `to target a user, we can send them a URL containing our payload`.

## DOM XSS
While `reflected XSS` sends the input data to the back-end server through HTTP requests, DOM XSS is completely processed on the client-side through JavaScript. DOM XSS occurs when JavaScript is used to change the page source through the `Document Object Model (DOM)`.

## Source & Sink
The `Source` is the JavaScript object that takes the user input, and it can be any input parameter like a URL parameter or an input field, as we saw above.

The `Sink` is the function that writes the user input to a DOM Object on the page. If the `Sink` function does not properly sanitize the user input, it would be vulnerable to an XSS attack.

Some of the commonly used JavaScript functions to write to DOM objects are:
- `document.write()`
- `DOM.innerHTML`
- `DOM.outerHTML`

Furthermore, some of the `jQuery` library functions that write to DOM objects are:
- `add()`
- `after()`
- `append()`