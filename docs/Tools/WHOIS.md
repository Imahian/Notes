# WHOIS

Protocol and command-line tool for querying public registration databases. Returns ownership, registration dates, DNS servers, and contact info for domains and IP ranges.

## Installation

Pre-installed on most Linux/macOS systems. On Debian/Ubuntu:
```bash
sudo apt install whois
```

## Basic usage

```bash
# Domain lookup
whois example.com

# IP address lookup
whois 8.8.8.8

# Specific WHOIS server
whois -h whois.arin.net 8.8.8.8
```

## Key fields in output

| Field | Description |
|-------|-------------|
| `Domain Name` | Queried domain |
| `Registry Domain ID` | Unique domain identifier in registry |
| `Registrar` | Organization managing the registration |
| `Creation Date` | When the domain was first registered |
| `Expiration Date` | When registration expires |
| `Updated Date` | Last modification date |
| `Name Servers` | DNS servers authoritative for the domain |
| `Status` | Domain state (active, clientHold, pendingDelete, etc.) |
| `Registrant` | Owner name/org (often redacted for privacy) |
| `Admin / Tech Email` | Contact emails (often redacted) |

## IP WHOIS

```bash
whois 8.8.8.8
# Returns: ASN, netblock owner (Google), country, abuse contact
```

Regional registries (ARIN, RIPE, APNIC, LACNIC, AFRINIC) hold IP block data.

## What to look for during recon

```bash
whois target.com | grep -iE "registrar|name server|creation|expir|registrant|email|phone"
```

- **Registrar** → hosting/registrar relationship
- **Name servers** → often reveals CDN, hosting provider, or managed DNS
- **Creation date** → very new domain = higher risk of phishing
- **Expiry soon** → potential for domain hijacking
- **Contact emails** → useful for social engineering scope or OSINT

## Complementary tools

| Tool | Use |
|------|-----|
| `nslookup` | Resolve domain → IP or IP → domain |
| `dig` | Detailed DNS record queries (A, MX, TXT, NS) |
| `host` | Quick DNS lookups |
| DNSDumpster | Visual WHOIS + DNS map |
| Netcraft | WHOIS + server history + tech stack |

```bash
# Typical passive recon sequence
whois target.com
dig target.com ANY
nslookup -type=mx target.com
```

## WHOIS privacy / GDPR note

Since GDPR (2018), many registrars redact registrant personal data. Use historical WHOIS services (DomainTools, ViewDNS.info) to find pre-redaction records.
