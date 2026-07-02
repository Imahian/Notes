# Attacking Web Applications with Ffuf

Fast web fuzzer written in Go. Used for directory discovery, parameter fuzzing, vhost enumeration, and filter bypass.

## Core Usage

```bash
# Directory fuzzing
ffuf -u http://TARGET/FUZZ -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt

# Extension fuzzing
ffuf -u http://TARGET/indexFUZZ -w /usr/share/seclists/Discovery/Web-Content/web-extensions.txt

# Page fuzzing (with extension)
ffuf -u http://TARGET/FUZZ.php -w wordlist.txt

# Recursive fuzzing
ffuf -u http://TARGET/FUZZ -w wordlist.txt -recursion -recursion-depth 2

# Subdomain/vhost fuzzing
ffuf -u http://TARGET -H "Host: FUZZ.target.com" -w subdomains.txt

# GET parameter fuzzing
ffuf -u "http://TARGET/page.php?FUZZ=value" -w params.txt

# POST data fuzzing
ffuf -u http://TARGET/login -X POST -d "user=admin&pass=FUZZ" -w passwords.txt -H "Content-Type: application/x-www-form-urlencoded"
```

## Filtering Results

```bash
# Filter by response code
ffuf ... -fc 404

# Filter by size
ffuf ... -fs 1234

# Filter by word count
ffuf ... -fw 10

# Match specific codes only
ffuf ... -mc 200,301,302

# Filter by regex in response
ffuf ... -fr "Not Found"
```

## Wordlists

| Purpose | Path |
|---------|------|
| Directories | `/usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt` |
| Extensions | `/usr/share/seclists/Discovery/Web-Content/web-extensions.txt` |
| Parameters | `/usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt` |
| Subdomains | `/usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt` |
