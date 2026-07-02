# Bug Bounty Hunting Process

Structured approach to bug bounty hunting — from program selection and scope analysis to report writing and submission.

## Program Selection

```
Platforms:
- HackerOne     → enterprise programs, high payouts
- Bugcrowd      → many programs, tiered rewards
- Intigriti     → European companies
- YesWeHack     → European focus
- Immunefi      → Web3 / blockchain, very high payouts

Criteria for picking a program:
- Wide scope (*.target.com beats target.com/page only)
- High average bounty
- Active triage (fast response time)
- Hall of fame or reputation points
```

## Scope Analysis

```bash
# Extract all domains from scope
# In-scope: *.example.com, api.example.com, *.staging.example.com
# Out-of-scope: test.example.com, admin.example.com (explicitly excluded)

# Rules:
# - Never test out-of-scope assets
# - Check if rate limiting is permitted
# - Check if automated scanning is allowed
# - Confirm if third-party integrations are in scope
```

## Recon Checklist

```
1. Subdomain enumeration (subfinder, amass, crt.sh)
2. Port scan on discovered hosts (nmap)
3. Directory brute force (ffuf, dirsearch)
4. Technology fingerprint (whatweb, wappalyzer)
5. JavaScript analysis (find endpoints, tokens, APIs)
6. Google dorking (site:target.com filetype:pdf inurl:admin)
7. GitHub leaks (github.com/search?q=target.com)
8. Shodan/Censys passive scan
```

## Vulnerability Assessment Priority

```
P1 (Critical) → RCE, SQLi with data exfil, Auth bypass admin, Account takeover
P2 (High)     → SQLi read-only, SSRF internal, XSS stored on sensitive page
P3 (Medium)   → CSRF on critical function, IDOR limited scope, Open redirect
P4 (Low)      → Self-XSS, info disclosure (stack trace, version headers)
P5 (Info)     → Missing security headers, content type sniffing
```

## Report Writing

```markdown
# Bug Report Template

**Vulnerability:** [Type] in [Endpoint]
**Severity:** Critical / High / Medium / Low
**CVSS Score:** 9.8 (example)
**CWE:** CWE-89 (SQL Injection)

## Summary
One paragraph — what the bug is and what impact it has.

## Steps to Reproduce
1. Navigate to https://target.com/login
2. Enter `' OR 1=1-- -` in the username field
3. Observe authentication bypass

## Impact
Describe what an attacker can do. Be specific. Include actual exfiltrated data (sanitized).

## Proof of Concept
[Screenshot or video]
[curl command that reproduces the bug]

## Recommended Fix
Parameterized queries / input validation / etc.
```

## Responsible Disclosure

- Report **before** public disclosure
- Give vendor reasonable time to fix (90 days standard)
- Don't access/exfiltrate user data beyond proving the vulnerability
- Don't perform DoS or destructive tests
