# HTB Machines

Full compromise writeups for retired HackTheBox machines. Each entry covers the complete attack chain from enumeration to root.

## Structure per Machine

```
machine-name/
├── README.md     ← Full writeup
└── img/          ← Screenshots
```

## Standard Toolchain

```bash
# Port scan
sudo nmap -p- --open -sS --min-rate 5000 -n -Pn <IP> -oG allPorts

# Service scan on discovered ports
nmap -sCV -p<ports> <IP> -oN targeted

# Web enumeration
gobuster dir -u http://<IP> -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
ffuf -u http://<IP>/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt

# Privilege escalation
./linpeas.sh
sudo -l
find / -perm -4000 2>/dev/null
```

## Machines

| Machine | OS | Difficulty | Tags |
|---------|-----|------------|------|
| [Spectra](Spectra/) | Linux | Easy | `web` `wordpress` `privesc` |
