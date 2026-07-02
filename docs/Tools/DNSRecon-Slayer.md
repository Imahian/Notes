# DNSRecon

Open-source DNS enumeration and security auditing tool. Performs detailed DNS queries to map domain infrastructure and detect misconfigurations.

**GitHub:** https://github.com/darkoperator/dnsrecon

## Installation

```bash
sudo apt install dnsrecon
# or
pip3 install dnsrecon
```

## What it finds

| Record type | Description |
|-------------|-------------|
| A / AAAA | IPv4 / IPv6 addresses |
| MX | Mail servers |
| NS | Name servers |
| TXT | SPF, DKIM, verification records |
| SOA | Start of Authority — zone info |
| Zone transfer | Full DNS zone dump (if server misconfigured) |
| Subdomains | Via brute-force wordlist |
| Reverse DNS | IP → hostname resolution |

## Core commands

```bash
# Standard record enumeration
dnsrecon -d example.com

# Zone transfer attempt
dnsrecon -d example.com -t axfr

# Subdomain brute force
dnsrecon -d example.com -t brt

# Reverse DNS sweep on a range
dnsrecon -r 192.168.1.0/24 -t rvl

# Google enumeration
dnsrecon -d example.com -t goo

# Save results to JSON
dnsrecon -d example.com -j output.json

# Save results to CSV
dnsrecon -d example.com --csv output.csv
```

## Scan types (`-t`)

| Type | Description |
|------|-------------|
| `std` | Standard record lookup (default) |
| `axfr` | Zone transfer attempt |
| `brt` | Brute-force subdomain enumeration |
| `goo` | Google scraping for subdomains |
| `rvl` | Reverse lookup on IP range |
| `snoop` | Cache snooping against nameserver |
| `tld` | TLD expansion |

## Complementary tools

| Tool | Use |
|------|-----|
| `dig` | Manual DNS query with fine-grained control |
| `fierce` | Subdomain-focused DNS scanner |
| `nmap` | Port/service scan after DNS recon |
| `dnsdumpster.com` | Visual passive DNS map |
| `subfinder` | Fast passive subdomain enumeration |
