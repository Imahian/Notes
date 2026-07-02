# Using Web Proxies

Web proxies intercept HTTP/S traffic between browser and server, enabling manual inspection and modification of every request and response.

## Burp Suite

```
Setup:
1. Proxy → Options → 127.0.0.1:8080
2. Browser → set HTTP proxy to 127.0.0.1:8080
3. Install Burp CA certificate (http://burp → CA Certificate)
4. Intercept → On
```

### Key Tabs

| Tab | Purpose |
|-----|---------|
| Proxy | Intercept and modify live traffic |
| Repeater | Manually replay and modify single requests |
| Intruder | Automated fuzzing with payloads |
| Scanner | Passive/active vulnerability scan (Pro only) |
| Decoder | Encode/decode base64, URL, HTML, hex |
| Comparer | Diff two requests/responses |
| Logger | Full request log |

### Common Workflows

```
Intercept → modify → forward
Right-click request → Send to Repeater → modify → Send
Right-click request → Send to Intruder → set § positions → load payload → Attack
```

## OWASP ZAP

```bash
# Launch
zaproxy &

# Automated scan
zap-baseline.py -t https://target.com -r report.html

# Spider
Tools → Spider → Start Scan
```

## curl as a Proxy-Aware Client

```bash
# Route curl through Burp
curl -x http://127.0.0.1:8080 http://target.com/page

# Ignore SSL errors (Burp cert not installed)
curl -x http://127.0.0.1:8080 -k https://target.com/page

# Replay Burp request with curl
curl -s -X POST "http://target.com/login" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -H "Cookie: PHPSESSID=abc123" \
  -d "user=admin&pass=test"
```

## Intercepting Mobile Traffic

```bash
# Route Android/iOS through Burp
# 1. Set same Burp proxy (your-ip:8080) on device
# 2. Install Burp CA cert on device
# 3. For certificate pinning: use Frida SSL pinning bypass
```
