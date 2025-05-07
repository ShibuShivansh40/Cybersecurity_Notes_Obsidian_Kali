![[Pasted image 20250507111907.png]]

#### Knowledge

Authentication based on knowledge factors relies on something that the user knows to prove their identity. The user provides information such as passwords, passphrases, PINs, or answers to security questions.

#### Ownership

Authentication based on ownership factors relies on something the user possesses. The user proves their identity by proving the ownership of a physical object or device, such as ID cards, security tokens, or smartphones with authentication apps. 

#### Inherence

Lastly, authentication based on inherence factors relies on something the user is or does. This includes biometric factors such as fingerprints, facial patterns, and voice recognition, or signatures. Biometric authentication is highly effective since biometric traits are inherently tied to an individual user.

| Knowledge                   | Ownership         | Inherence         |
| --------------------------- | ----------------- | ----------------- |
| Password                    | ID card           | Fingerprint       |
| PIN                         | Security Token    | Facial Pattern    |
| Answer to Security Question | Authenticator App | Voice Recognition |

## Enumerating Users
When we attempt to log in to the lab with an invalid username such as `abc`, we can see the following error message:

   

![](https://academy.hackthebox.com/storage/modules/269/bf/userenum_1.png)

On the other hand, when we attempt to log in with a registered user such as `htb-stdnt` and an invalid password, we can see a different error:

   

![](https://academy.hackthebox.com/storage/modules/269/bf/userenum_2.png)

Let us exploit this difference in error messages returned and use SecLists's wordlist `xato-net-10-million-usernames.txt` to enumerate valid users with `ffuf`. We can specify the wordlist with the `-w` parameter, the POST data with the `-d` parameter, and the keyword `FUZZ` in the username to fuzz valid users. Finally, we can filter out invalid users by removing responses containing the string `Unknown user`:

  Enumerating Users

```shell-session
ShibuShivansh@htb[/htb]$ ffuf -w /opt/useful/seclists/Usernames/xato-net-10-million-usernames.txt -u http://172.17.0.2/index.php -X POST -H "Content-Type: application/x-www-form-urlencoded" -d "username=FUZZ&password=invalid" -fr "Unknown user"

<SNIP>

[Status: 200, Size: 3271, Words: 754, Lines: 103, Duration: 310ms]
    * FUZZ: consuelo
```