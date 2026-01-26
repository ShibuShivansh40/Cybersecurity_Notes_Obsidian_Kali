## Authentication

Authentication, at its core, is the validation of your identity by presenting a combination of four factors to a validation mechanism. They are:

1. `Something you know`: a password, passcode, PIN, passphrase, etc.
2. `Something you have`: an ID card, smart card, trusted device/phone, etc.
3. `Something you are`: biometric characteristics such as fingerprint, face recognition, iris/retina, voice, etc.
4. `Somewhere you are`: geolocation, IP address, etc.


Passwords are commonly `hashed` when stored, in order to provide some protection in the event they fall into the hands of an attacker. `Hashing` is a mathematical function which transforms an arbitrary number of input bytes into a (typically) fixed-size output; common examples of hash functions are `MD5`, and `SHA-256`.

MD5 and SHA-256 Hashes for the password `Basketball07!` is : 
```
┌──(shibushivansh㉿shibu)-[~]
└─$ echo -n Basketball07! | md5sum
edbb31a5c657514f6e1ea4a36c37ba53  -
                                                      
┌──(shibushivansh㉿shibu)-[~]
└─$ echo -n Basketball07! | sha256sum 
68985876f17e209c926cfca43bb23f766e0c361093951e90e200f0e67c028290  -
```

Hash functions are designed to work in `one direction`. This means it should not be possible to figure out what the original password was based on the hash alone. When attackers attempt to do this, it is called `password cracking`. Common techniques are to use `rainbow tables`, to perform `dictionary attacks`, and typically as a last resort, to perform `brute-force attacks`.

## Rainbow Tables

Rainbow tables are large pre-compiled maps of input and output values for a given hash function. These can be used to very quickly identify the password if its corresponding hash has already been mapped.

A `salt`, in cryptographic terms, is a random sequence of bytes added to a password before it is hashed. To maximize impact, salts should not be reused, e.g. for all passwords stored in one database. For example, if the salt `Th1sIsTh3S@lt_` is prepended to the same password, the MD5 hash would now be as follows:

```
┌──(shibushivansh㉿shibu)-[~]
└─$ echo -n Th1sIsTh3S@lt_Basketball07! | md5sum
981ae4a020ed1ae1bce6e5cf5ba09d9b  -
```


### JohnTheRipper
**Single Crack Mode :**
Imagine we as attackers came across the file `passwd` with the following contents:

```
r0lf:$6$ues25dIanlctrWxg$nZHVz2z4kCy1760Ee28M1xtHdGoy0C2cYzZ8l2sVa1kIa8K9gAcdBP.GI6ng/qA4oaMrgElZ1Cb9OeXO4Fvy3/:0:0:Rolf Sebastian:/home/r0lf:/bin/bash
```

Based on the contents of the file, it can be inferred that the victim has the username `r0lf`, the real name `Rolf Sebastian`, and the home directory `/home/r0lf`. Single crack mode will use this information to generate candidate passwords and test them against the hash. We can run the attack with the following command:

```shell-session
ShibuShivansh@htb[/htb]$ john --single passwd

Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 256/256 AVX2 4x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
[...SNIP...]        (r0lf)     
1g 0:00:00:00 DONE 1/3 (2025-04-10 07:47) 12.50g/s 5400p/s 5400c/s 5400C/s NAITSABESFL0R..rSebastiannaitsabeSr
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```

In this case, the password hash was successfully cracked.

**Wordlist Mode :** `ShibuShivansh@htb[/htb]$ john --wordlist=<wordlist_file> <hash_file>`

**Incremental Mode :** `Incremental mode` is a powerful, brute-force-style password cracking mode that generates candidate passwords based on a statistical model ([Markov chains](https://en.wikipedia.org/wiki/Markov_chain)). It is designed to test all character combinations defined by a specific character set, prioritizing more likely passwords based on training data.

This mode is the most exhaustive, but also the most time-consuming. It generates password guesses dynamically and does not rely on a predefined wordlist, in contrast to wordlist mode. Unlike purely random brute-force attacks, Incremental mode uses a statistical model to make educated guesses, resulting in a significantly more efficient approach than naïve brute-force attacks.

The basic syntax is:
```shell-session
ShibuShivansh@htb[/htb]$ john --incremental <hash_file>
```

To know about Incremental Mode of JohnTheRipper, use this command : `grep '# Incremental modes' -A 100 /etc/john/john.conf `

**Identifying Hash Formats : ** 
```   
┌──(shibushivansh㉿shibu)-[~]
└─$ hashid -j 193069ceb0461e1d40d216e32c79c704  
Analyzing '193069ceb0461e1d40d216e32c79c704'
[+] MD2 [JtR Format: md2]
[+] MD5 [JtR Format: raw-md5]
[+] MD4 [JtR Format: raw-md4]
[+] Double MD5 
[+] LM [JtR Format: lm]
[+] RIPEMD-128 [JtR Format: ripemd-128]
[+] Haval-128 [JtR Format: haval-128-4]
[+] Tiger-128 
[+] Skein-256(128) 
[+] Skein-512(128) 
[+] Lotus Notes/Domino 5 [JtR Format: lotus5]
[+] Skype 
[+] Snefru-128 [JtR Format: snefru-128]
[+] NTLM [JtR Format: nt]
[+] Domain Cached Credentials [JtR Format: mscach]
[+] Domain Cached Credentials 2 [JtR Format: mscach2]
[+] DNSSEC(NSEC3) 
[+] RAdmin v2.x [JtR Format: radmin]                                   
```

|**Hash format**|**Example command**|**Description**|
|---|---|---|
|afs|`john --format=afs [...] <hash_file>`|AFS (Andrew File System) password hashes|
|bfegg|`john --format=bfegg [...] <hash_file>`|bfegg hashes used in Eggdrop IRC bots|
|bf|`john --format=bf [...] <hash_file>`|Blowfish-based crypt(3) hashes|
|bsdi|`john --format=bsdi [...] <hash_file>`|BSDi crypt(3) hashes|
|crypt(3)|`john --format=crypt [...] <hash_file>`|Traditional Unix crypt(3) hashes|
|des|`john --format=des [...] <hash_file>`|Traditional DES-based crypt(3) hashes|
|dmd5|`john --format=dmd5 [...] <hash_file>`|DMD5 (Dragonfly BSD MD5) password hashes|
|dominosec|`john --format=dominosec [...] <hash_file>`|IBM Lotus Domino 6/7 password hashes|
|EPiServer SID hashes|`john --format=episerver [...] <hash_file>`|EPiServer SID (Security Identifier) password hashes|
|hdaa|`john --format=hdaa [...] <hash_file>`|hdaa password hashes used in Openwall GNU/Linux|
|hmac-md5|`john --format=hmac-md5 [...] <hash_file>`|hmac-md5 password hashes|
|hmailserver|`john --format=hmailserver [...] <hash_file>`|hmailserver password hashes|
|ipb2|`john --format=ipb2 [...] <hash_file>`|Invision Power Board 2 password hashes|
|krb4|`john --format=krb4 [...] <hash_file>`|Kerberos 4 password hashes|
|krb5|`john --format=krb5 [...] <hash_file>`|Kerberos 5 password hashes|
|LM|`john --format=LM [...] <hash_file>`|LM (Lan Manager) password hashes|
|lotus5|`john --format=lotus5 [...] <hash_file>`|Lotus Notes/Domino 5 password hashes|
|mscash|`john --format=mscash [...] <hash_file>`|MS Cache password hashes|
|mscash2|`john --format=mscash2 [...] <hash_file>`|MS Cache v2 password hashes|
|mschapv2|`john --format=mschapv2 [...] <hash_file>`|MS CHAP v2 password hashes|
|mskrb5|`john --format=mskrb5 [...] <hash_file>`|MS Kerberos 5 password hashes|
|mssql05|`john --format=mssql05 [...] <hash_file>`|MS SQL 2005 password hashes|
|mssql|`john --format=mssql [...] <hash_file>`|MS SQL password hashes|
|mysql-fast|`john --format=mysql-fast [...] <hash_file>`|MySQL fast password hashes|
|mysql|`john --format=mysql [...] <hash_file>`|MySQL password hashes|
|mysql-sha1|`john --format=mysql-sha1 [...] <hash_file>`|MySQL SHA1 password hashes|
|NETLM|`john --format=netlm [...] <hash_file>`|NETLM (NT LAN Manager) password hashes|
|NETLMv2|`john --format=netlmv2 [...] <hash_file>`|NETLMv2 (NT LAN Manager version 2) password hashes|
|NETNTLM|`john --format=netntlm [...] <hash_file>`|NETNTLM (NT LAN Manager) password hashes|
|NETNTLMv2|`john --format=netntlmv2 [...] <hash_file>`|NETNTLMv2 (NT LAN Manager version 2) password hashes|
|NEThalfLM|`john --format=nethalflm [...] <hash_file>`|NEThalfLM (NT LAN Manager) password hashes|
|md5ns|`john --format=md5ns [...] <hash_file>`|md5ns (MD5 namespace) password hashes|
|nsldap|`john --format=nsldap [...] <hash_file>`|nsldap (OpenLDAP SHA) password hashes|
|ssha|`john --format=ssha [...] <hash_file>`|ssha (Salted SHA) password hashes|
|NT|`john --format=nt [...] <hash_file>`|NT (Windows NT) password hashes|
|openssha|`john --format=openssha [...] <hash_file>`|OPENSSH private key password hashes|
|oracle11|`john --format=oracle11 [...] <hash_file>`|Oracle 11 password hashes|
|oracle|`john --format=oracle [...] <hash_file>`|Oracle password hashes|
|pdf|`john --format=pdf [...] <hash_file>`|PDF (Portable Document Format) password hashes|
|phpass-md5|`john --format=phpass-md5 [...] <hash_file>`|PHPass-MD5 (Portable PHP password hashing framework) password hashes|
|phps|`john --format=phps [...] <hash_file>`|PHPS password hashes|
|pix-md5|`john --format=pix-md5 [...] <hash_file>`|Cisco PIX MD5 password hashes|
|po|`john --format=po [...] <hash_file>`|Po (Sybase SQL Anywhere) password hashes|
|rar|`john --format=rar [...] <hash_file>`|RAR (WinRAR) password hashes|
|raw-md4|`john --format=raw-md4 [...] <hash_file>`|Raw MD4 password hashes|
|raw-md5|`john --format=raw-md5 [...] <hash_file>`|Raw MD5 password hashes|
|raw-md5-unicode|`john --format=raw-md5-unicode [...] <hash_file>`|Raw MD5 Unicode password hashes|
|raw-sha1|`john --format=raw-sha1 [...] <hash_file>`|Raw SHA1 password hashes|
|raw-sha224|`john --format=raw-sha224 [...] <hash_file>`|Raw SHA224 password hashes|
|raw-sha256|`john --format=raw-sha256 [...] <hash_file>`|Raw SHA256 password hashes|
|raw-sha384|`john --format=raw-sha384 [...] <hash_file>`|Raw SHA384 password hashes|
|raw-sha512|`john --format=raw-sha512 [...] <hash_file>`|Raw SHA512 password hashes|
|salted-sha|`john --format=salted-sha [...] <hash_file>`|Salted SHA password hashes|
|sapb|`john --format=sapb [...] <hash_file>`|SAP CODVN B (BCODE) password hashes|
|sapg|`john --format=sapg [...] <hash_file>`|SAP CODVN G (PASSCODE) password hashes|
|sha1-gen|`john --format=sha1-gen [...] <hash_file>`|Generic SHA1 password hashes|
|skey|`john --format=skey [...] <hash_file>`|S/Key (One-time password) hashes|
|ssh|`john --format=ssh [...] <hash_file>`|SSH (Secure Shell) password hashes|
|sybasease|`john --format=sybasease [...] <hash_file>`|Sybase ASE password hashes|
|xsha|`john --format=xsha [...] <hash_file>`|xsha (Extended SHA) password hashes|
|zip|`john --format=zip [...] <hash_file>`|ZIP (WinZip) password hashes|

**Cracking Files :**
It is also possible to crack password-protected or encrypted files with JtR. Multiple `"2john"` tools come with JtR that can be used to process files and produce hashes compatible with JtR. The generalized syntax for these tools is:

```shell-session
ShibuShivansh@htb[/htb]$ <tool> <file_to_crack> > file.hash
```

Some of the tools included with JtR are:

| **Tool**                | **Description**                               |
| ----------------------- | --------------------------------------------- |
| `pdf2john`              | Converts PDF documents for John               |
| `ssh2john`              | Converts SSH private keys for John            |
| `mscash2john`           | Converts MS Cash hashes for John              |
| `keychain2john`         | Converts OS X keychain files for John         |
| `rar2john`              | Converts RAR archives for John                |
| `pfx2john`              | Converts PKCS#12 files for John               |
| `truecrypt_volume2john` | Converts TrueCrypt volumes for John           |
| `keepass2john`          | Converts KeePass databases for John           |
| `vncpcap2john`          | Converts VNC PCAP files for John              |
| `putty2john`            | Converts PuTTY private keys for John          |
| `zip2john`              | Converts ZIP archives for John                |
| `hccap2john`            | Converts WPA/WPA2 handshake captures for John |
| `office2john`           | Converts MS Office documents for John         |
| `wpa2john`              | Converts WPA/WPA2 handshakes for John         |
