# Information Gathering - Web Edition

Passive and active recon techniques for web targets — DNS, WHOIS, subdomain enumeration, fingerprinting, and crawling.

## Passive Recon (no direct contact with target)

```bash
# WHOIS
whois target.com

# DNS records
dig target.com ANY
dig target.com MX
dig target.com NS
nslookup -type=any target.com

# Reverse DNS
dig -x <IP>

# Certificate transparency (subdomains)
curl "https://crt.sh/?q=%.target.com&output=json" | jq '.[].name_value' | sort -u

# Google dorks
site:target.com
site:target.com filetype:pdf
site:target.com inurl:admin
cache:target.com
```

## Subdomain Enumeration

```bash
# Passive — via APIs (no DNS queries)
subfinder -d target.com
amass enum -passive -d target.com
assetfinder target.com

# Active — DNS brute force
ffuf -u http://FUZZ.target.com -H "Host: FUZZ.target.com" -w subdomains.txt -mc 200,301,302
gobuster dns -d target.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```

## Fingerprinting

```bash
# Web server and technology
whatweb http://target.com
curl -I http://target.com           # Check Server, X-Powered-By headers

# WAF detection
wafw00f http://target.com

# CMS detection
wpscan --url http://target.com      # WordPress
droopescan scan drupal -u http://target.com
joomscan --url http://target.com
```

## Crawling & Spidering

```bash
# Wayback machine for old URLs
waybackurls target.com | sort -u

# Crawl with hakrawler
echo "https://target.com" | hakrawler -subs

# Robots and sitemap
curl http://target.com/robots.txt
curl http://target.com/sitemap.xml
```
