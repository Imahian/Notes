# eWPT

**eLearnSecurity Web Application Penetration Tester** — covers manual web application testing aligned with OWASP methodology.

## Exam Format

- **Duration:** 7 days
- **Format:** Black-box web app assessment
- **Deliverable:** Written penetration testing report

## Syllabus

| Domain | Topics |
|--------|--------|
| HTTP Protocol | Methods, headers, cookies, sessions, encoding |
| Web Enumeration | Directory brute-force, parameter discovery, spider |
| Cross-Site Scripting | Reflected, stored, DOM-based; filter bypass |
| SQL Injection | Error-based, blind, time-based, UNION |
| Authentication Attacks | Brute force, credential stuffing, default creds |
| Session Management | Cookie theft, session fixation, CSRF |
| File Inclusion | LFI, RFI, path traversal |
| Other Vulnerabilities | IDOR, SSRF, open redirect, clickjacking |
| Burp Suite | Proxy, Repeater, Intruder, Scanner |

## Key Payloads

```
# XSS test
"><script>alert(1)</script>
<img src=x onerror=alert(1)>

# SQLi test
' OR 1=1-- -
' UNION SELECT null,null,null-- -

# LFI
../../../../../../etc/passwd
php://filter/convert.base64-encode/resource=index.php
```

## Tools

`burpsuite` `sqlmap` `ffuf` `nikto` `wfuzz` `curl`
