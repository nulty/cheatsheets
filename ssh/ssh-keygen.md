# SSH keygen

* Don't use DSA or ECDSA
* If using RSA, use > 3000 bits
* Recommend using ED25519

## Creating a new key

### Wizard (with defaults)

**Command**
```
$ ssh-keygen
```

This will start the wizard with defaults
Default type: rsa

**Prompts**
1. Confirm/change the location and name of the key ($HOME/.ssh/id_rsa)
2. Enter a passphrase (highly recommended 10-30 chars)

```
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/nulty/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/nulty/.ssh/id_rsa.
Your public key has been saved in /home/nulty/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:9ekZyodm7mN0EmEvzwnc+JU9+u9tFpuVVQ6CeEDh448 nulty@mycomp
The key's randomart image is:
+---[RSA 2048]----+
|       .++ .     |
|       .. = . . .|
|        o+.= . =.|
|       . o*.o.o.+|
|        S  B+o. +|
|         +o+*+ o.|
|        E.Bo+ . =|
|         +o.   ++|
|         oo.   +=|
+----[SHA256]-----+
```

### Specify key details

**Command**
```
$ ssh-keygen -t ed25519 -C "nulty@inulty.com" -a 200 -b 256 -f ~/.ssh/id_mysite_ed25519
```
**Options**
1. `-t` Type: Options are RSA, DSA, ECDSA, ED25519 (ED25519 recommended)
2. `-C` Comment: defaults to "user@hostname" of the machine the key generated on. Maybe use a domain you own for the hostname?
3. `-f` Filename / path: normally in "$HOME/.ssh/name_of_key"
4. `-b` Bits: Complexity and security of the key (bits >= 256 for ED25519)
5. `-a` KDF: Key Derivation Rounds: higher means slower & more secure


## Editing a key
### Change passphrase


**Command**
```
$ ssh-keygen -p ~/.ssh/id_ed25519
```
1. `-p` Change passphrase

### Change Comment

Comment is designed to describe the key (default is `user@hostname`)

**Command**
```
$ ssh-keygen -c ~/.ssh/id_ed25519
```
**Options**
1. `-c` Change comment

## Print public key from private key

```
$ ssh-keygen -y -f ~/.ssh/id_nulty_ed25519
Enter passphrase:
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIIUxRdkd9oMVycXplRpjizH2sPMu+fG4FhK3HU5JGXYw
```

## Fingerprint

### SHA256
**Command**
```
$ ssh-keygen -l -E sha256 -f ./id_rsa
2048 SHA256:HHQbSm+Chl0ygj4MQjeqhozb+0G+2pkHA+gSUPLEAzc nulty@mycomp (RSA)
```

### MD5
**Command**

```
$ ssh-keygen -l -E md5 -f ./id_rsa
2048 MD5:2e:1a:5f:dc:29:a6:d5:99:e6:ef:4f:0d:c1:a0:a0:15 nulty@mycomp (RSA)
```
1. `-l` Show fingerprint 
2. `-f` Specify key (file can be the private or public key)
3. `-E` Hashing function [sha256 (default), md5]


### Randomart
```
$ ssh-keygen -l -v -f ./id_rsa
2048 SHA256:HHQbSm+Chl0ygj4MQjeqhozb+0G+2pkHA+gSUPLEAzc nulty@mycomp (RSA)
+---[RSA 2048]----+
|+=E+. o + o      |
|+=*..+ B + o     |
|o*... + + +      |
|B =  . . +       |
|=+ o.   S        |
|o+ oo            |
|o . oo           |
|   o =.          |
|  oo*.           |
+----[SHA256]-----+
```
1. `-v` Print randomart for the key

### Bubblebabble fingerprint
```
$ ssh-keygen -B -f ./id_rsa
2048 ximes-sihur-tomol-zemak-depuf-manyr-corif-bamac-cumug-fapas-cyxox My New Key (RSA)
```
1. `-B` Specify bubblebabble style fingerprint

## Exporting

### RFC4716 (default)
```
$ ssh-keygen -e -m RFC4716 -f ./id_rsa
---- BEGIN SSH2 PUBLIC KEY ----
Comment: "2048-bit RSA, converted by nulty@mycomp from OpenSSH"
AAAAB3NzaC1yc2EAAAADAQABAAABAQC9Hco5otiHLUBMO2Zuv1cgg/b2A9gGQCK7rlRKQn
aFk/PBc0IuNj8IoTixmW2SOiNEH8d75Xg345b7FkiIfW9wNO89gxkVqFIieTpp75JiG5p/
KRvWbPmx2HKsM0nj2d2bDcCeQO/lr8r/uGDVMWIUsxW+c7Uvj9MDDHSnwVbYEgcOPGWmM/
l/sfFtHkEKhGWGRUBlKEKUbsKGV/QlkyvdUo2VModiRV7v1ZQ3E6ZR1Qnr6M6Qh20Lqz7/
0vvgs7utq43Or1eHl7Q4o1JEtC/c/ffhtyY8an5IYiWbDGjb3tyJoUqFZQdyYeQ1CpcLNz
MzdycZNQPiK2/m6cxioBsZ
---- END SSH2 PUBLIC KEY ----
```

### PKCS8
```
$ ssh-keygen -e -m PKCS8 -f ./id_rsa
-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAvR3KOaLYhy1ATDtmbr9X
IIP29gPYBkAiu65USkJ2hZPzwXNCLjY/CKE4sZltkjojRB/He+V4N+OW+xZIiH1v
cDTvPYMZFahSInk6ae+SYhuafykb1mz5sdhyrDNJ49ndmw3AnkDv5a/K/7hg1TFi
FLMVvnO1L4/TAwx0p8FW2BIHDjxlpjP5f7HxbR5BCoRlhkVAZShClG7Chlf0JZMr
3VKNlTKHYkVe79WUNxOmUdUJ6+jOkIdtC6s+/9L74LO7rauNzq9Xh5e0OKNSRLQv
3P334bcmPGp+SGIlmwxo297ciaFKhWUHcmHkNQqXCzczM3cnGTUD4itv5unMYqAb
GQIDAQAB
-----END PUBLIC KEY-----
```

### PEM
```
$ ssh-keygen -e -m PEM -f ./id_rsa
-----BEGIN RSA PUBLIC KEY-----
MIIBCgKCAQEAvR3KOaLYhy1ATDtmbr9XIIP29gPYBkAiu65USkJ2hZPzwXNCLjY/
CKE4sZltkjojRB/He+V4N+OW+xZIiH1vcDTvPYMZFahSInk6ae+SYhuafykb1mz5
sdhyrDNJ49ndmw3AnkDv5a/K/7hg1TFiFLMVvnO1L4/TAwx0p8FW2BIHDjxlpjP5
f7HxbR5BCoRlhkVAZShClG7Chlf0JZMr3VKNlTKHYkVe79WUNxOmUdUJ6+jOkIdt
C6s+/9L74LO7rauNzq9Xh5e0OKNSRLQv3P334bcmPGp+SGIlmwxo297ciaFKhWUH
cmHkNQqXCzczM3cnGTUD4itv5unMYqAbGQIDAQAB
-----END RSA PUBLIC KEY-----
```

## Delete keys from server

This will remove the public key from the known_hosts file of the HOST server

```
$ ssh-keygen -R some_ip_address -f ~/.ssh/id_ed25519
```
**Options**
1. `-R` Specify ip or domain to remove the key from

## Certificates
TODO

## Miscellaneous

### Accept defaults (sysadmins)
(I never use this, seems only for initialising a server)


```
$ ssh-keygen -A
ssh-keygen: generating new host keys: RSA Could not save your public key in /etc/ssh/ssh_host_rsa_key.dr9FgkmdGU: Permission denied

```
**Options**
1. `-A` This is used by system administration scripts to generate new host keys
