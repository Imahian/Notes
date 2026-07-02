# eCPPT

**eLearnSecurity Certified Professional Penetration Tester** — intermediate-level cert covering network pentesting, web exploitation, post-exploitation, and pivoting.

## Exam Format

- **Duration:** 7 days lab + 7 days report
- **Format:** Black-box engagement with a full network
- **Deliverable:** Professional penetration testing report

## Syllabus

| Domain | Topics |
|--------|--------|
| System Security | Buffer overflows (x86), shellcoding, SEH exploits |
| Network Security | Nmap, enumeration, password attacks, Metasploit |
| PowerShell for Pentesters | Windows automation, bypass techniques |
| Linux Exploitation | SUID, cron, sudo, kernel exploits |
| Web Application Security | OWASP Top 10, SQLi, XSS, file inclusion |
| Wi-Fi Security | WPA2 attacks, evil twin, capture handshakes |
| Ruby for Pentesters | Scripting exploits in Ruby |

## Pivoting Techniques Covered

```bash
# SSH dynamic port forward (SOCKS proxy)
ssh -D 9050 user@pivot-host

# Metasploit route
route add <subnet> <subnet_mask> <session_id>
use auxiliary/server/socks4a

# Proxychains
proxychains nmap -sT -Pn <internal-ip>
```

## Key Tools

`metasploit` `msfvenom` `nmap` `burpsuite` `hydra` `john` `proxychains` `impacket`
