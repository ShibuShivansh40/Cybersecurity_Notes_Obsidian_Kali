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


