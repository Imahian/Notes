# JavaScript Deobfuscation

Techniques for reversing obfuscated JavaScript to discover hidden functionality, API keys, hardcoded credentials, and logic flaws.

## Common Obfuscation Methods

| Method | Description |
|--------|-------------|
| Minification | Whitespace and variable names stripped |
| Packing (eval/p,a,c,k,e,d) | Code compressed into eval string |
| Encoding | base64, hex, unicode escapes |
| String splitting | `"hel"+"lo"` |
| Character code | `String.fromCharCode(72,101,108,108,111)` |

## Deobfuscation Tools

```bash
# Online
# https://beautifier.io       — format and indent minified JS
# https://obf-io.deobfuscate.io — automated deobfuscation
# https://deobfuscate.relative.im — handles eval/packer
# https://www.dcode.fr/javascript-unobfuscator

# Browser DevTools
# F12 → Sources → Pretty print {} button
# F12 → Console → paste code, call eval manually

# Node.js
node -e "eval(require('fs').readFileSync('obf.js','utf8'))"
```

## Manual Techniques

```javascript
// Replace eval with console.log to see decoded string
eval(function(p,a,c,k,e,d){...})
// → change eval to console.log:
console.log(function(p,a,c,k,e,d){...})

// Decode base64
atob("aGVsbG8=")                   // browser console
echo "aGVsbG8=" | base64 -d       // bash

// Decode hex string
"\x68\x65\x6c\x6c\x6f"            // → "hello" in browser console

// fromCharCode array
String.fromCharCode(72,101,108,108,111)   // → "Hello"
```

## Finding Secrets

```bash
# Extract strings from JS file
strings script.js | grep -iE "api|key|token|secret|pass|auth"

# Search for interesting patterns
grep -E "(api_key|apiKey|access_token|secret|password)\s*[:=]" *.js

# Download all JS files from page
wget -r -l 1 -A "*.js" http://target.com
```
