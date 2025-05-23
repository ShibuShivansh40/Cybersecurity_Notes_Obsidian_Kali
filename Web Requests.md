### Structure of URL
![[InternalJPEGS/Pasted image 20250326143830.png]]
### HTTP Flow
![[InternalJPEGS/Pasted image 20250326143400.png]]

> **Note:** Our browsers usually first look up records in the local '`/etc/hosts`' file, and if the requested domain does not exist within it, then they would contact other DNS servers. We can use the '`/etc/hosts`' to manually add records to for DNS resolution, by adding the IP followed by the domain name.


### cURL
1. Command used to send a basic HTTP Request to URL : `curl inlanefreight.com`
2. Command used to download content of a particular file : `curl -O inlanefreight.com/index.html`
3. Command used to skip the SSL Certificate check and run cURL : `curl -k https://inlanefreight.com`
4. Command to run cURL in the verbose mode : `curl inlanefreight.com -v`
5. Command to view the Response Headers provided by the server : `curl -I https//www.inlanefreight.com`
6. Command to view both the Response Headers and body : `curl -i https://www.inlanefreight.com`
7. Command used to set request headers : `curl http://www.inlanefreight.com -H "Content-Type: application/json'`
8. Command used to set User-Agent would be : `curl https://www.inlanefreight.com -A 'Mozilla/5.0`
9. Command used to provide credentials : `curl -u admin:admin http://<SERVER_IP>:<PORT>/` or `curl http://admin:admin@<SERVER_IP>:<PORT>/`
10. Command used to initiate a POST Request with Body : `curl -X POST -d 'username=admin&password=admin' https://<SERVER_IP>:<PORT>/`
11. Command used to make a POST Request along with Cookie, Content-Type and Body: `curl -X POST -b "PHPSESSID=n95r8o8nihq3o5qghinihduq5d" -H "Content-Type: application/json" -d '{"search":"flag"}'  http://94.237.54.176:44683/search.php?search=flag `

### HTTPS Flow
![[InternalJPEGS/Pasted image 20250326143830.png]]

> **Note:** Depending on the circumstances, an attacker may be able to perform an HTTP downgrade attack, which downgrades HTTPS communication to HTTP, making the data transferred in clear-text. This is done by setting up a Man-In-The-Middle (MITM) proxy to transfer all traffic through the attacker's host without the user's knowledge. However, most modern browsers, servers, and web applications protect against this attack.

### HTTP Request & Response
![[InternalJPEGS/Pasted image 20250326144036.png]]
![[InternalJPEGS/Pasted image 20250326144313.png]]

### APIs
There are several types of APIs. Many APIs are used to interact with a database, such that we would be able to specify the requested table and the requested row within our API query, and then use an HTTP method to perform the operation needed. For example, for the `api.php` endpoint in our example, if we wanted to update the `city` table in the database, and the row we will be updating has a city name of `london`, then the URL would look something like this:
```bash
curl -X PUT http://<SERVER_IP>:<PORT>/api.php/city/london
```

To properly format JSON in the response, we can pip the command with `jq` :
```bash
curl -s http://<SERVER_IP>:<PORT>/api.php/city/london | jq

[
  {
    "city_name": "London",
    "country_name": "(UK)"
  }
]
```

>Note : **Note:** The HTTP `PATCH` method may also be used to update API entries instead of `PUT`. To be precise, `PATCH` is used to partially update an entry (only modify some of its data "e.g. only city_name"), while `PUT` is used to update the entire entry. We may also use the HTTP `OPTIONS` method to see which of the two is accepted by the server, and then use the appropriate method accordingly. In this section, we will be focusing on the `PUT` method, though their usage is quite similar.

Updating the data :
```bash
curl -X PUT http://<SERVER_IP>:<PORT>/api.php/city/london -d '{"city_name":"New_HTB_City", "country_name":"HTB"}' -H 'Content-Type: application/json'
```

Deleting the data : 
```bash
curl -X DELETE http://<SERVER_IP>:<PORT>/api.php/city/New_HTB_City
```

