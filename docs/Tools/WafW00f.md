# WafW00f

WAF (Web Application Firewall) detection tool. Sends crafted requests to a target and analyzes responses to identify the WAF protecting it.

**GitHub:** https://github.com/EnableSecurity/wafw00f

## Installation

```bash
pip install wafw00f
# or
sudo apt install wafw00f
```

## Basic usage

```bash
# Detect WAF on a target
wafw00f https://example.com

# Test all known WAFs (slower but more thorough)
wafw00f -a https://example.com

# Verbose output
wafw00f -v https://example.com

# Output in JSON
wafw00f -o output.json https://example.com

# Test multiple targets from file
wafw00f -i targets.txt
```

## What it detects

WafW00f fingerprints 100+ WAFs including:

| WAF | Vendor |
|-----|--------|
| Cloudflare | Cloudflare |
| AWS WAF | Amazon |
| ModSecurity | Open Source |
| Akamai Kona | Akamai |
| Imperva Incapsula | Imperva |
| F5 BIG-IP ASM | F5 |
| Barracuda WAF | Barracuda |
| Sucuri | Sucuri |

```
# Example output
[*] Checking https://example.com
[+] The site https://example.com is behind Cloudflare (Cloudflare Inc.) WAF.
[~] Number of requests: 7
```

## How it works

1. Sends normal baseline request
2. Sends crafted malicious payloads (SQLi, XSS probes)
3. Compares response headers, body, and status codes
4. Matches patterns against WAF signature database

## Use in pentesting

- **Before active testing** — know if WAF is present; adjust payloads accordingly
- **WAF bypass planning** — identify WAF type → research known bypass techniques
- **Scope documentation** — document security controls in pentest report

## Complementary tools

| Tool | Use |
|------|-----|
| `nmap --script http-waf-detect` | Alternative WAF detection via Nmap NSE |
| Burp Suite | Manual WAF behavior analysis via HTTP proxy |
| `sqlmap --tamper` | Tamper scripts to bypass detected WAFs |
| `cloudflair` | Find origin IP behind Cloudflare |
