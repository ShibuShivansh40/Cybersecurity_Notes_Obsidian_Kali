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


# Key Learnings
- To start API testing, you first need to find out as much information about the API as possible, to discover its attack surface.
- You should identify API endpoints.
- Look for patterns that suggest API endpoints in the URL structure, such as `/api/`
To change the content type, modify the `Content-Type` header, then reformat the request body accordingly.

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

