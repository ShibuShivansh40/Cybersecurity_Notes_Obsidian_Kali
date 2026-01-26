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

