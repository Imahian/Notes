# Sublist3r

Passive subdomain enumeration tool. Queries search engines and public APIs to build a subdomain list without directly probing the target.

**GitHub:** https://github.com/aboul3la/Sublist3r

## Installation

```bash
git clone https://github.com/aboul3la/Sublist3r.git
cd Sublist3r && pip install -r requirements.txt

# or
sudo apt install sublist3r
```

## Basic usage

```bash
# Enumerate subdomains
sublist3r -d example.com

# Save output to file
sublist3r -d example.com -o subdomains.txt

# Verbose mode
sublist3r -d example.com -v

# Enable bruteforce in addition to passive search
sublist3r -d example.com -b
```

## Options

| Option | Description |
|--------|-------------|
| `-d` | Target domain |
| `-o <file>` | Save results to file |
| `-v` | Verbose output |
| `-b` | Enable brute-force mode |
| `-p <ports>` | Scan discovered subdomains on specified ports |
| `-e <engines>` | Comma-separated list of engines to use |
| `-t <threads>` | Thread count (default: 10) |

## Data sources

Sublist3r queries: Google, Bing, Yahoo, Baidu, Ask, Netcraft, VirusTotal, ThreatCrowd, SSL certificates, PassiveDNS

## Limitations

- Passive only by default — misses non-indexed subdomains
- Search engine rate limits can slow results
- For better coverage, combine with active tools

## Better alternatives (modern)

| Tool | Notes |
|------|-------|
| `subfinder` | Faster, more sources, actively maintained |
| `amass` | Most thorough; passive + active modes |
| `assetfinder` | Lightweight, fast |
| `chaos` | ProjectDiscovery's massive subdomain dataset |

```bash
# Recommended modern workflow
subfinder -d example.com -o passive.txt
amass enum -passive -d example.com -o amass.txt
cat passive.txt amass.txt | sort -u > all_subdomains.txt
```
