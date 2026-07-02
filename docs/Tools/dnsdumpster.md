# DNSDumpster

Web-based passive DNS reconnaissance tool. Maps DNS infrastructure of a target domain using public data — no direct contact with target servers.

**URL:** https://dnsdumpster.com

## What it finds

| Record type | Info |
|-------------|------|
| A | IPv4 addresses for the domain and subdomains |
| MX | Mail servers |
| NS | Name servers |
| TXT | SPF, DKIM, and other TXT records |
| Subdomains | Associated subdomains discovered from public sources |
| IP geolocation | Country/region for each IP |

## Usage

1. Go to https://dnsdumpster.com
2. Enter domain (e.g. `example.com`)
3. Results show DNS records, subdomain map, and IP distribution
4. Export as PDF for offline analysis

## Key features

- **Passive only** — no requests sent to target; reduces detection risk
- **Free** — no account required
- **Visual output** — infrastructure map showing how DNS components relate
- **Fast** — results in seconds

## Use cases

- Subdomain discovery before active testing
- Identify mail/name servers for phishing simulation scope
- Map attack surface during initial recon phase

## Limitations

- Coverage depends on public data sources — may miss recent subdomains
- No brute-force capability (use `subfinder`, `amass`, or `dnsrecon -t brt` for that)
- Rate-limited on free tier

![DNSDumpster example output](https://i.imgur.com/Ftn4uN5.png)
