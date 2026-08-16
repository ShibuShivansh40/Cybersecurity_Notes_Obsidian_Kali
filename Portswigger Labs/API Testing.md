*A concise, in-depth overview based on PortSwigger's Web Security Academy.*

## 1. Introduction to API Testing
APIs (Application Programming Interfaces) enable software systems to communicate. Since most dynamic websites use APIs (particularly RESTful and JSON APIs), testing them is critical for preventing vulnerabilities that undermine confidentiality, integrity, and availability.

## 2. API Reconnaissance
The first step in API testing is identifying the attack surface by discovering API endpoints and understanding how to interact with them.

* **Identify Endpoints:** Locate where the API receives requests (e.g., `GET /api/books`).
* **Determine Interaction Mechanics:** Identify supported input data (optional and compulsory parameters), HTTP methods, accepted media formats, rate limits, and authentication mechanisms.

## 3. API Documentation
Documentation can be **human-readable** (for developers) or **machine-readable** (structured formats like JSON/YAML for automation).
* **Discovering Documentation:** Use tools like Burp Scanner or manual browsing to find exposed documentation. Common paths include `/api`, `/swagger/index.html`, and `/openapi.json`.
* **Analyzing Machine-Readable Docs:** Use tools like Burp Scanner, the OpenAPI Parser BApp, Postman, or SoapUI to parse and test documented endpoints.

## 4. Uncovering Hidden Attack Surfaces
Sometimes API documentation is incomplete, inaccurate, or hidden. You must actively search for undocumented endpoints and parameters.
* **Manual & Automated Browsing:** Look for API patterns (e.g., `/api/`) in URLs. Analyze JavaScript files for hidden endpoint references (tools like the JS Link Finder BApp are highly effective).
* **Testing HTTP Methods:** Endpoints may support multiple actions (GET, POST, PUT, PATCH, DELETE, OPTIONS). Testing different methods on low-priority objects can reveal hidden functionality.
* **Testing Content Types:** Changing the `Content-Type` header (e.g., swapping JSON for XML) might bypass defenses, trigger informative errors, or expose different processing logic.
* **Brute-Forcing with Intruder:** Use Burp Intruder with wordlists based on common naming conventions to find hidden endpoints (e.g., replacing `/update` with `/delete`).
* **Discovering Hidden Parameters:** Use Burp Intruder, the Param miner BApp (which can guess up to 65,536 names per request), or the Content discovery tool to find undocumented parameters.

## 5. Mass Assignment Vulnerabilities
Mass assignment (or auto-binding) occurs when a framework automatically binds request parameters to fields on an internal object. This can allow users to update parameters they shouldn't have access to.

* **Identification:** Examine API responses (like a `GET` request) to find hidden object fields (e.g., `"isAdmin": "false"`).
* **Exploitation:** Inject the identified field into a `PATCH` or `PUT` request (e.g., sending `"isAdmin": true`). If the application lacks adequate validation, this can lead to privilege escalation.

## 6. Prevention Strategies
To secure APIs during development:
* Secure and restrict access to API documentation if it is not meant to be public.
* Keep documentation strictly up-to-date.
* Implement strict allowlists for permitted HTTP methods.
* Validate expected content types for every request and response.
* Use generic error messages to prevent information leakage.
* Apply protective measures consistently across *all* versions of an API, not just the latest production release.
* **Prevent Mass Assignment:** Explicitly allowlist properties that users are permitted to update and strictly blocklist sensitive properties.

| **Method**  | **Description**                                                                                                                                                                                            |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **GET**     | Retrieves data from a server. It should be an idempotent operation, meaning it only fetches data and does not change the state of the resource.                                                            |
| **POST**    | Submits data to the server, typically to create a new resource or trigger a specific backend process.                                                                                                      |
| **PUT**     | Completely replaces an existing resource with the provided data. If the resource does not exist, it may create it.                                                                                         |
| **PATCH**   | Applies partial modifications to an existing resource. Unlike `PUT`, you only send the specific fields you want to update.                                                                                 |
| **DELETE**  | Removes the specified resource from the server.                                                                                                                                                            |
| **OPTIONS** | Requests information about the communication options available for the target endpoint. It is frequently used in Cross-Origin Resource Sharing (CORS) preflight requests.                                  |
| **HEAD**    | Functions exactly like a `GET` request, but the server only returns the HTTP headers and omits the response body. It is useful for checking file sizes or resource existence without downloading the data. |
| **TRACE**   | Performs a diagnostic loop-back test. The server echoes the received request back to the client, which can be useful for debugging but is often disabled to prevent Cross-Site Tracing (XST) attacks.      |
| **CONNECT** | Establishes a two-way network tunnel to the server. It is primarily used to facilitate SSL/TLS-encrypted communication (HTTPS) through an unencrypted HTTP proxy.                                          |
#### Identifying supported content types

API endpoints often expect data in a specific format. They may therefore behave differently depending on the content type of the data provided in a request. Changing the content type may enable you to:

- Trigger errors that disclose useful information.
- Bypass flawed defenses.
- Take advantage of differences in processing logic. For example, an API may be secure when handling JSON data but susceptible to injection attacks when dealing with XML.
To change the content type, modify the `Content-Type` header, then reformat the request body accordingly.

# Key Learnings
- To start API testing, you first need to find out as much information about the API as possible, to discover its attack surface.
- You should identify API endpoints.
- Look for patterns that suggest API endpoints in the URL structure, such as `/api/`
- ***URL Parameter Pollution*** : PHP parses the last parameter only. ASP.NET combines both parameters. Node.js / Express parses the first parameter only.


## Lab - Exploiting an API Endpoint
Aim : Delete the user named "Carlos"
Solution:
Logged into provided credentials and then I was trying to know about API Documentation and found "unauthorized" when visiting `/api/users` and when I removed `user` and then we got the below documentation and we hence need to design a Request for the same.
![[Pasted image 20260816230026.png]]

And hence I just need to make the below request :
![[Pasted image 20260816230506.png]]

## Lab - Finding and exploiting an unused API endpoint
Aim - Exploit a hidden API endpoint to buy a **Lightweight l33t Leather Jacket**.
Solution -
When we are checking out the product in Cart, it checks the funds present in the my account and then throw an error INSUFFICIENT FUNDS, so we need to check how the API is working in order to know where things could exploited to either change funds in my account or the price of the Jacket.

In the Target Section, I just found one Request with `api/prodcuts/1/price`, so from here we will try to get some information regarding the API. On doing a lot of modification with a lot of Endpoints, I found something really interesting :
![[Pasted image 20260816232859.png]]
After doing in change in the Content-Type, I found that we can get more information about it:
![[Pasted image 20260816233130.png]]
And hence I was able to change the price :
![[Pasted image 20260816233156.png]]
![[Pasted image 20260816233243.png]]


## Lab - Exploiting Mass Assignment Vulnerability
Aim - Buy a Leather Jacket exploiting vulnerability
Solution -
While checking the Target, I found only one endpoint that is going to use `api` and hence I got the direction to start with the exploitation.
![[Pasted image 20260817004526.png]]
And then I started to exploit the Headers and finding a way to get the exact response and get the Price equal to zero, so that I could check out easily.
![[Pasted image 20260817004402.png]]And hence I just had to manipulate the Discount to 100% and then I just got the Jacket for free and solved  :
![[Pasted image 20260817005136.png]]


# Server-Side Parameter Pollution in APIs
*A concise overview based on PortSwigger's Web Security Academy.*

## 1. Concept Overview
**Server-Side Parameter Pollution (SSPP)** occurs when a web application processes user input and embeds it into a server-side request (such as communicating with an internal API or backend service) without proper validation or encoding. This allows an attacker to manipulate the parameters sent to the internal API, potentially bypassing access controls, altering application logic, or accessing unauthorized data.

## 2. Testing the Query String
To test for SSPP, you need to observe how the server handles unexpected characters or parameters injected into the input. 

* **Truncating Query Strings:** You can attempt to cut off the rest of the intended backend request by injecting a URL-encoded fragment identifier (`#`, encoded as `%23`). If the application drops subsequent parameters, it indicates the input is being appended directly to an internal request.
* **Injecting Invalid Parameters:** Add dummy parameters (e.g., `&foo=bar`) to a request. If the application's response changes or throws a detailed error, it may indicate that the internal API is attempting to process the injected parameter.
* **Injecting Valid Parameters:** If you discover hidden parameters during your API reconnaissance, you can inject them to see if you can manipulate the internal logic (e.g., appending `&admin=true`).
* **Overriding Existing Parameters (HPP):** Send multiple parameters with the exact same name (e.g., `?username=victim&username=attacker`). Different backend technologies process duplicate parameters differently:
    * **PHP/Apache:** Usually takes the *last* parameter.
    * **ASP.NET:** Usually concatenates them with a comma (`victim,attacker`).
    * **Node.js/Express:** Usually creates an array (`[victim, attacker]`) or takes the first parameter depending on configuration.

## 3. Testing REST Paths
APIs often place parameter values directly into the REST URL path (e.g., `/api/users/{username}`). You can test these by injecting URL-encoded path traversal sequences or query delimiters.
* **Path Traversal:** Injecting `%2f` (encoded `/`) or `%2e%2e%2f` (encoded `../`) might allow you to traverse the backend API's directory structure if the frontend server decodes it before forwarding the request.
* **Query Injection:** Injecting a URL-encoded `?` (`%3f`) might trick the backend into treating the rest of the intended URL path as a query string.

## 4. Testing Structured Data Formats
Parameter pollution isn't limited to query strings; it can also occur in structured data like JSON or XML.
* **JSON Parameter Pollution:** Injecting duplicate keys into a JSON payload (e.g., `{"userid": 1, "userid": 2}`). Similar to query strings, the JSON parser's behavior determines which value is processed (often the last one).

## 5. Prevention Strategies
To secure APIs against Server-Side Parameter Pollution:
* **Apply Strict URL Encoding:** Ensure all user input is properly URL-encoded before it is embedded into any server-side HTTP request.
* **Input Validation:** Implement strict allowlists for all user input. Validate the expected format, type, and length of the data.
* **Safe API Clients:** Use built-in libraries or SDKs that automatically handle parameter binding and encoding safely, rather than manually concatenating strings to build internal API requests.
* **Consistent Parsing:** Ensure that the frontend gateway and backend internal APIs handle duplicate parameters in the exact same way to prevent logic discrepancies.
## Lab - Exploiting Server-Side Parameter Pollution in a Query String
Aim - Log in as `administrator` and delete `carlos`
Solution - 
The only query string found was in Product Query, so I'll be trying to exploit that. Tried a lot of things, hence had to see the solution to understand that.

I tried to follow the solution, but it was confusing. So, while I was doing the recon part I saw something like `reset_token`, so I thought there must be something around that. But we needed that Token, so I started to follow the solution.

So I used an Intruder Attack to get onto something and I used a simple tactic present that was to add up a field into the request and then just use the Sniper Attack to find the valid fields. 
![[Pasted image 20260817045843.png]]

So, on running the attack it simply gave us `email` as the field and then we inserted that as well. But as there as something related to that reset_token, so I added that on to the field and found the below response.
![[Pasted image 20260817045249.png]]

Then I went to the browser to get to somewhere where I could log in into the Admin Dashboard, so according to the Web Application, whenever there is a Email sent for Password reset, we receive a link with reset tokens, so I inserted that reset_token into the endpoint as `/forgot-password?reset_token=token` and hence I got a way to enter a new password for the Administrator and then I logged in with the new Password and then I just deleted Carlos' Account.

