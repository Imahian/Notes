# Assessment Methodologies

Structured approach to security assessments — from passive recon through vulnerability scanning.

## Methodology Phases

### 1. Passive Information Gathering

Collect data about the target **without** direct interaction. Uses public sources only — no packets sent to the target.

| Tool | Purpose |
|------|---------|
| DNSRecon | DNS record enumeration (A, MX, NS, TXT, zone transfer attempts) |
| whois | Domain ownership, registration dates, registrar, DNS servers |
| DNSDumpster | Visual DNS map — subdomains, IPs, MX, NS records |
| Shodan | Internet-connected device search; find exposed services |
| Netcraft | Web server history, technology stack, WHOIS reports |
| Sublist3r | Subdomain enumeration via search engines and APIs |
| theHarvester | Email, host, and subdomain discovery from public sources |

```bash
# Passive DNS recon
dnsrecon -d target.com
whois target.com
theHarvester -d target.com -b all
```

### 2. Service Discovery

Identify active hosts and open ports on the target network.

| Tool | Purpose |
|------|---------|
| nmap | Port scanning, service detection, OS fingerprinting |
| netcat | Manual port probing, banner grabbing |
| masscan | High-speed port scanning across large ranges |

```bash
# Discover live hosts
nmap -sn 192.168.1.0/24

# Fast full port scan
nmap -p- --open --min-rate 5000 -n -Pn <target>

# Service + version detection
nmap -sCV -p<ports> <target>
```

### 3. Service Enumeration

Enumerate services in depth to extract versions, configurations, and potential entry points.

| Tool | Purpose |
|------|---------|
| nmap -sCV | Script scan + version detection on open ports |
| nikto | Web server vulnerability scanner |
| gobuster / ffuf | Web directory and file brute force |
| enum4linux | SMB/Samba enumeration (users, shares, policies) |

```bash
# Web enumeration
nikto -h http://target.com
gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt

# SMB enumeration
enum4linux -a target.com
```

### 4. Vulnerability Scanning

Scan discovered services for known CVEs and misconfigurations.

| Tool | Purpose |
|------|---------|
| OpenVAS | Open-source full vulnerability scanner |
| Nessus | Commercial vulnerability scanner (widely used) |
| nmap NSE | Script-based vuln checks (`--script vuln`) |

```bash
# Nmap vuln scripts
nmap --script vuln -p<ports> <target>
```

## Practical Workflow

```
1. whois + DNSRecon + theHarvester   → passive recon
2. nmap -sn                           → host discovery
3. nmap -p- --min-rate 5000           → port discovery
4. nmap -sCV -p<ports>                → service fingerprinting
5. nikto / gobuster / enum4linux      → service enumeration
6. OpenVAS / Nessus / nmap --script vuln → vulnerability scan
```
