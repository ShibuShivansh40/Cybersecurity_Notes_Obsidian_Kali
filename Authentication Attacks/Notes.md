# Authentication & Sessions
**Session Management** is a process by which a server maintains the state of an entity interacting with it. This is required for a server to remember how to react to subsequent requests throughout a transaction. Sessions are maintained on the server by a session identifier which can be passed back and forth between the client and server when transmitting and receiving requests. Sessions should be unique per user and computationally very difficult to predict.

Password Length
- **Minimum** length for passwords should be enforced by the application. Passwords **shorter than 8 characters** are considered to be weak ([NIST SP800-63B](https://pages.nist.gov/800-63-3/sp800-63b.html)).
- **Maximum** password length should be **at least 64 characters** to allow passphrases ([NIST SP800-63B](https://pages.nist.gov/800-63-3/sp800-63b.html)). Note that certain implementations of hashing algorithms may cause [long password denial of service](https://www.acunetix.com/vulnerabilities/web/long-password-denial-of-service/).

> By sending a very long password (1.000.000 characters) it's possible to cause a denial a service attack on the server. This may lead to the website becoming unavailable or unresponsive. Usually this problem is caused by a vulnerable password hashing implementation. When a long password is sent, the password hashing process will result in CPU and memory exhaustion.

Block common and previously breached passwords
- [Pwned Passwords](https://haveibeenpwned.com/Passwords) is a service where passwords can be checked against previously breached passwords. Details on the API [are here](https://haveibeenpwned.com/API/v3#PwnedPasswords).
- Alternatively, you can download the [Pwned Passwords](https://haveibeenpwned.com/Passwords) database [using this mechanism](https://github.com/HaveIBeenPwned/PwnedPasswordsDownloader?tab=readme-ov-file#what-is-haveibeenpwned-downloader) to host it yourself.
- Other top password lists are available but there is no guarantee as to how updated they are:
    - [Various password lists](https://github.com/danielmiessler/SecLists/tree/master/Passwords) hosted by SecLists from Daniel Miessler.
    - Static copy of the top 100,000 passwords from "Have I Been Pwned" hosted by NCSC in [text](https://www.ncsc.gov.uk/static-assets/documents/PwnedPasswordsTop100k.txt) and [JSON](https://www.ncsc.gov.uk/static-assets/documents/PwnedPasswordsTop100k.json) format.

#### Authentication Responses[¶](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html#authentication-responses "Permanent link")
Using any of the authentication mechanisms (login, password reset, or password recovery), an application must respond with a generic error message regardless of whether:

- The user ID or password was incorrect.
- The account does not exist.
- The account is locked or disabled.

The account registration feature should also be taken into consideration, and the same approach of a generic error message can be applied regarding the case in which the user exists.

The objective is to prevent the creation of a [discrepancy factor](https://cwe.mitre.org/data/definitions/204.html), allowing an attacker to mount a user enumeration action against the application.

It is interesting to note that the business logic itself can bring a discrepancy factor related to the processing time taken. Indeed, depending on the implementation, the processing time can be significantly different according to the case (success vs failure) allowing an attacker to mount a [time-based attack](https://en.wikipedia.org/wiki/Timing_attack) (delta of some seconds for example).

#### CAPTCHA[¶](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html#captcha "Permanent link")
The use of an effective CAPTCHA can help to prevent automated login attempts against accounts. However, many CAPTCHA implementations have weaknesses that allow them to be solved using automated techniques or can be outsourced to services that can solve them. As such, the use of CAPTCHA should be viewed as a defense-in-depth control to make brute-force attacks more time-consuming and expensive, rather than as a preventative.

It may be more user-friendly to only require a CAPTCHA be solved after a small number of failed login attempts, rather than requiring it from the very first login.

### SAML[¶](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html#saml "Permanent link")
Security Assertion Markup Language (SAML) is often considered to compete with OpenId. The most recommended version is 2.0 since it is very feature-complete and provides strong security. Like OpenId, SAML uses identity providers, but unlike OpenId, it is XML-based and provides more flexibility. SAML is based on browser redirects which send XML data. Furthermore, SAML isn't only initiated by a service provider; it can also be initiated from the identity provider. This allows the user to navigate through different portals while still being authenticated without having to do anything, making the process transparent.

While OpenId has taken most of the consumer market, SAML is often the choice for enterprise applications because there are few OpenId identity providers which are considered enterprise-class (meaning that the way they validate the user identity doesn't have high standards required for enterprise identity). It is more common to see SAML being used inside of intranet websites, sometimes even using a server from the intranet as the identity provider.

In the past few years, applications like SAP ERP and SharePoint (SharePoint by using Active Directory Federation Services 2.0) have decided to use SAML 2.0 authentication as an often preferred method for single sign-on implementations whenever enterprise federation is required for web services and web applications.



# JWT Tokens
### Header
The header _typically_ consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.
```
{
  "alg": "HS256",
  "typ": "JWT"
}
```

### Payload
The second part of the token is the payload, which contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: _registered_, _public_, and _private_ claims.

- [**Registered claims**](https://tools.ietf.org/html/rfc7519#section-4.1): These are a set of predefined claims which are not mandatory but recommended, to provide a set of useful, interoperable claims. Some of them are: **iss** (issuer), **exp** (expiration time), **sub** (subject), **aud** (audience), and [others](https://tools.ietf.org/html/rfc7519#section-4.1).
- [**Public claims**](https://tools.ietf.org/html/rfc7519#section-4.2): These can be defined at will by those using JWTs. But to avoid collisions, they should be defined in the [IANA JSON Web Token Registry](https://www.iana.org/assignments/jwt/jwt.xhtml) or be defined as a URI that contains a collision-resistant namespace.
- [**Private claims**](https://tools.ietf.org/html/rfc7519#section-4.3): These are the custom claims created to share information between parties that agree on using them and are neither _registered_ or _public_ claims.
```
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```


### Signature
To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

For example, if you want to use the HMAC SHA256 algorithm, the signature will be created in the following way:
```
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

The signature is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.

# Authentication Attacks [Add them to WAPT Checklist]
### Password Based Authentication
1. Brute-forcing the username to get a valid username by checking precisely over the response packets.
2. If the Server blocks your IP, then try to use a Header in the Response Packet named as `X-Forarded-For:` and use a Pitchfork Attack and provide this with a random number set. Keep an eye on the response use the settings like : Grep-by Match, Response Timing Delays.
3. We can try checking with multiple login attempts and see to it, if it blocks the IP after a particular failed attempts then we can try add the actual credentials after each attempt, so that it removes the block from the IP Address and we can try to access that using a Pitchfork Attack where word list has genuine credentials after each brute-forced ones.
4. Also, if there is an issue of Account Blocking then what we can do is, we can do User Enumeration by checking the amount of time taken by the User when it is pass for almost 5 times, using 2 payloads, one for Username and one just as Null Payload, that would help us in getting the user and then we can get the Password.
5. When doing brute-force attack, check for minute changes in the responses and errors. Even a . matters there, and that could lead to big vulnerabilities, if there is an account locking then we need to see that was there any response where we didn't receive any error while we saw errors in other passwords.
6. When we see account locking and IP Blocking in an authentication attack, do look out for if there is a JSON going on then we can manipulate it by the following way : 
	1. 1. With Burp running, investigate the login page. Notice that the `POST /login` request submits the login credentials in `JSON` format. Send this request to Burp Repeater.
	2. In Burp Repeater, replace the single string value of the password with an array of strings containing all of the candidate passwords. For example: `"username" : "carlos", "password" : [ "123456", "password", "qwerty" ... ]`
	3. Send the request. This will return a 302 response.
	4. Right-click on this request and select **Show response in browser**. Copy the URL and load it in the browser. The page loads and you are logged in as `carlos`.
	5. Click **My account** to access Carlos's account page and solve the lab.

### Multi-factor Authentication
1. Just when we get onto a MFA Verification Page, try to switch to a User Profile Page simply.
2. We can also check for the Packet's cookie section and if we found any identity of the user then tampering it would help for sure. Tamper that detail so that the instead of legitimate user some other user gets sent the MFA Codes and then brute-force those MFA Codes with the tampered identity cookie.
3. **Sometimes, there is an advanced Brute-force which rate-limits and resets the verification code, here we can use MACROS in Burp Suite :**
	1. With Burp running, log in as `carlos` and investigate the 2FA verification process. Notice that if you enter the wrong code twice, you will be logged out again. You need to use Burp's session handling features to log back in automatically before sending each request.
	2. In Burp, click **Settings** to open the **Settings** dialog, then click **Sessions**. In the **Session Handling Rules** panel, click **Add**. The **Session handling rule editor** dialog opens.
	3. In the dialog, go to the **Scope** tab. Under **URL Scope**, select the option **Include all URLs**.
	4. Go back to the **Details** tab and under **Rule Actions**, click **Add > Run a macro**.
	5. Under **Select macro** click **Add** to open the **Macro Recorder**. Select the following 3 requests:
	    `GET /login POST /login GET /login2`
	    Then click **OK**. The **Macro Editor** dialog opens.
	6. Click **Test macro** and check that the final response contains the page asking you to provide the 4-digit security code. This confirms that the macro is working correctly.
	7. Keep clicking **OK** to close the various dialogs until you get back to the main Burp window. The macro will now automatically log you back in as Carlos before each request is sent by Burp Intruder.
	8. Send the `POST /login2` request to Burp Intruder.
	9. In Burp Intruder, add a payload position to the `mfa-code` parameter.
	10. In the **Payloads** side panel, select the **Numbers** payload type. Enter the range 0 - 9999 and set the step to 1. Set the min/max integer digits to 4 and max fraction digits to 0. This will create a payload for every possible 4-digit integer.
	11. Click on **Resource pool** to open the **Resource pool** side panel. Add the attack to a resource pool with the **Maximum concurrent requests** set to `1`.
	12. Start the attack. Eventually, one of the requests will return a `302` status code. Right-click on this request and select **Show response in browser**. Copy the URL and load it in the browser.
	13. Click **My account** to solve the lab.

### Other Authentication Mechanisms
1. basically check for the Logged-in Cookie and try to decode it and what if we get certain parameters being present in it which could be brute-forced using Intruder.
2. While checking for Changing New Password, try putting incorrect password for two matching password fields. And you might find different ideas over that.

### OAuth 2.0 Authentication Vulnerabilities
#### Flawed CSRF protection

Although many components of the OAuth flows are optional, some of them are strongly recommended unless there's an important reason not to use them. One such example is the `state` parameter.

The `state` parameter should ideally contain an unguessable value, such as the hash of something tied to the user's session when it first initiates the OAuth flow. This value is then passed back and forth between the client application and the OAuth service as a form of CSRF token for the client application. Therefore, if you notice that the authorization request does not send a `state` parameter, this is extremely interesting from an attacker's perspective. It potentially means that they can initiate an OAuth flow themselves before tricking a user's browser into completing it, similar to a traditional CSRF attack. This can have severe consequences depending on how OAuth is being used by the client application.

Consider a website that allows users to log in using either a classic, password-based mechanism or by linking their account to a social media profile using OAuth. In this case, if the application fails to use the `state` parameter, an attacker could potentially hijack a victim user's account on the client application by binding it to their own social media account.