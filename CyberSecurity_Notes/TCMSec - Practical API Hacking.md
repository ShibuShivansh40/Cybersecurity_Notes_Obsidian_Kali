# Introduction
## What is an API
![[Pasted image 20250226153430.png]]

## Interacting with APIs
![[Pasted image 20250226160110.png]]
To interact with APIs, we could different approaches depending upon the type of webapp : 
1. Directly use the browser, by visiting the API Endpoint
2. Use Burp Proxy to gather the information about the Request and Packet.
3. Use Curl, to know about the Response.
4. Also, we can use Postman

## Types of APIS
![[Pasted image 20250226161208.png]]
Different HTTP Request Methods : 
- GET
- HEAD
- POST
- PUT
- DELETE
- CONNECT
- OPTIONS
- TRACE
- PATH


# Enumerating APIs
## Fuzzing APIs
Things to notice when starting to Fuzz:
1. Check if there is version number present and then check for the upgraded or downgraded versions of the given APIs : ![[Screenshot 2025-02-26 171003.png]]
2. Then check for different endpoints like in there, we have books and resources, we could think of some endpoint like stores, clients, ids etc.
3. Then we can see that there is a parameter named as `published` hence parameters like `unpublished`, `delete` etc might be present.

We can use `wfuzz` to check for the endpoints, using the command : `wfuzz -c -z file,<wordlist_path> --sc 200 'https://domain.com/api/v1/resources/books?show=FUZZ`

## Manual Enumeration
Go to the Developer Tools > Debugger and then check for different modules, config.js, JS File containing top-level API endpoints.

# Attacking Authorization
## Authorization
Authentication is the identity and Authorization is what are we allowed to do.


Basically if we are in a hotel, I can access a particular room depending on my ![[Screenshot 2025-02-26 181633.png]]
![[Screenshot 2025-02-26 181720.png]]

![[Screenshot 2025-02-26 181711.png]]

## BOLA Lab
Whenever see a URL and see the presence of the Object ID or Reference ID, and then we can see some information that could be changed on providing any other reference ID and without authorization errors, it allows us to get the results, then we could easily say that we found a Broken Object Level Authorization (BOLA) Vulnerability.

## BFLA Lab
It is all about having access to the functionalities that an authorized person must have by a simple user account.

# Attacking Authentication
It is all about who you're and proving your identity.
Basically, we can Brute-force the Panel using Burp Suite  Intruder with a password list of choice.

Then we can use ffuf for the same task to brute-force the credentials.

## Attacking Tokens
In this we should login into an account and wait for the cookies to be generated.
Gather the POST Request sent to login into the account. As we get a Token in the Response for verifying that correct User is logging in, we will then use Sequencer's Live Capture.

Then we'll configure it where we need to put the value of Token.

## JSON Web Tokens

![[Screenshot 2025-03-03 184358.png]]  
A JWT is sent in Response by specifying : `Authorization : Bearer <JWT-Token>`
Now to get the Authorization Token as  a Response, in the video he used : `curl -X PSOT http://domain.com  --header "Content-Type: application/json" --data '{"username" : "user", "password": "user" }'`

Now to use Hashcat to get the Secret Key for the JWT Token, we can brute-force it : `hashcat -a 0 -m 16500 <JWT_Token> <wordlist> --show`  | `-a` : for dictionary attack | `-m` : for mode selection (for JWT it is 16500)

`hashcat -a 0 -m 16500 eyJraWQiOiI0NmEwOTM2My1kNjgzLTQyYTMtOWJlNy1mMTkyYmY3NjMxMzQiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJwb3J0c3dpZ2dlciIsImV4cCI6MTc0MTM1NDgwNywic3ViIjoid2llbmVyIn0.6WUABGuPj6mmjCXbTt6QkcouH9teq1I-lmpFvJFKLzs --show`

After getting the Secret Key as the result, we'll try to make changes in the Header/Payload of the Token and try to tamper the requests.

And to send a Request to the Server we can type in the command like : `curl -i https://domain.com --Header 'Authorization: Bearer <JWT-Token>'`

## The JWT Toolkit 
Link : https://github.com/ticarpi/jwt_tool
It is a simple tool, just type in `jwt_tool` after the installation and provide it with desired JWT.
`jwt_tool <JWT_Token> -T` : This will allow us to modify the Token according to us.

`jwt_tool -t http://domains.com -rh 'Authorization: Bearer <JWT-Token> -M at`

**Broken Signature Response** : It means that if we hamper with the Secret Key even then Authenticated Responses can be received.
In the Wiki Page of Github, we get information about the Vulnerabilities that could be found.

# Injection
![[Pasted image 20250304145706.png]]
![[Pasted image 20250304145714.png]]
![[Screenshot 2025-03-04 145802.png]]

It goes by mentioning basic payloads for  testing the application : 
1. `?roast=5'` : It will tell us how the application responds when an unwilling input is provided to it.
2. `?roast=5' or 1=1` 
3. `?roast=5 UNION SELECT username, password from Users` : If we get an error regarding the issue in the number of columns, we'll try to manipulate that by providing `null` in the number of columns.
4. `?roast = 5 and sleep(10)` : This will put a delay of 10 seconds for the response to be received. - Time Based SQL Injection 
5. 

We can instead of using BurpSuite, use FFuF using the command : `ffuf -u 'http://localhost/v1/001.php?roast=FUZZ' -w /wordlist_dir/`

We should use SQLMap when we're onto some kind of SQLi  Vulnerability, using the command : `sqlmap -r req.txt` and append the request we want to play with into the text file.

And when everything has happened in the SQLMap, we could just simply write the command : `sqlmap -r req.txt --ignore-code 401 --dump`
## Login Bypass
Now while working with Login Forms we need to see the behavior of the Server and how it is throwing out errors.
Now according to the basic query of SQL : `SELECT * FROM User WHERE username=$username AND password=$password`
We need to make changes in our payload according to SQL.

## NoSQL Injection
![[Pasted image 20250304175338.png]]
![[Pasted image 20250304175419.png]]

In the below image we're trying to find an entry with `name` as `jeremy` and `password` not equal to `0`
![[Pasted image 20250304175458.png]]

First we need to know that the Application is using NoSQL then we can start to put some payloads and test how the application is responding.

 `/login?username=admin&password[$ne]=sdkfnskdn` : Here we have added a `$ne` that tells the server that show the output of the user with username `admin` and password not equal to the given value.

We can use `[$ne]` when parameter is present in the URL but when in the Body we need to pass it as JSON Object, then we'll do that by following payloads : 
![[Pasted image 20250304180153.png]]

Cracking JWT Tokens using jwt_tool : `jwt_tool -C -d <wordlist> "JWT-Token"`

# Mass Assignment
In this section, there are following things we need to analyze : 

1. Analyze the Code - Code Review
2. Check with Requests you're making
3. Check for HTTP Request Methods
4. Make changes in the User Privileges through Requests

# Server Side Request Forgery
![[Pasted image 20250305115418.png]]
![[Pasted image 20250305115434.png]]

Basically we need to trick the server to retrieve the data or to connect to the endpoint we want to connect to and that is usually `localhost`.

And also while hunting Real-World Applications, we should use a URL where if the Server exposes the data, it doesn't create any issue in it.

