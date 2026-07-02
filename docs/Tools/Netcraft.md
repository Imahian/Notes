# Netcraft

Internet security company providing web infrastructure intelligence, phishing detection, and domain/IP reporting services.

**Site Report:** https://sitereport.netcraft.com

## What Netcraft provides

| Feature | Description |
|---------|-------------|
| WHOIS lookup | Domain ownership, creation/expiry dates, registrar, DNS servers |
| Server history | Timeline of web server changes for a domain |
| Technology detection | Web server software (Apache, Nginx), OS, CMS, frameworks |
| Phishing detection | Flags domains involved in phishing or malware distribution |
| Risk assessment | Threat indicators associated with the domain |

## Usage

1. Go to https://sitereport.netcraft.com
2. Enter a domain or IP
3. Click **Search**
4. Review the full infrastructure report

## Key data points from a report

```
Domain:          example.com
Registrar:       GoDaddy
Created:         2004-01-15
Expires:         2025-01-15
Name servers:    ns1.example.com, ns2.example.com
Web server:      nginx/1.18.0
OS:              Linux
IP:              93.184.216.34
Hosting:         Edgecast Networks
Netblock owner:  Verizon Digital Media Services
First seen:      2004-02-01
```

## Use cases

- **Passive recon** — identify hosting provider, server stack, registrar without touching target
- **Phishing investigation** — check if domain is flagged as malicious
- **Attack surface mapping** — understand server history to find decommissioned endpoints
- **Technology profiling** — know the stack before probing for version-specific CVEs
