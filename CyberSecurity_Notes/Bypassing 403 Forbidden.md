For example we get an error like : `Access denied because of the xxx.xx.xx.xx Client IP`
Now what we can do is, we can try to change the IP using cURL : `curl -H 'X-FORWARDED-FOR: 127.0.0.1' http://domain.com/secrets`. Here we can also put the company's IP instead of localhost or some company's other VPN Addresses.

For example, if the server is using a blacklist technique to bypass the String we add in the URL, then we can try some techniques of Path Normalization like, instead of using `/secure/admin` we can type in `/secure/./admin` which points to the same folder/path of the website. If this particular technique is bypassed we can try to do one thing that is try with `/secure/../admin`.

![[Pasted image 20250630155017.png]]
For example in the above image, there is a 403 Forbidden Error because of Access Permissions. Now here we can see that the endpoints becomes `/v2/users/<integer>`. Things we can try now :
1. Try changing the Integer Value and try to bypass something if possible.
2. Try to back in the directory like to `/v2/users/` only, and check for the Server's behaviour
3. Try to Change the V

