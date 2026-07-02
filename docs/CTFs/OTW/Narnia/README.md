# Narnia

**Difficulty:** Intermediate | **Topics:** Binary exploitation — stack buffer overflows, shellcode, format strings, SUID

Introduction to binary exploitation in C. Programs are compiled with weakened protections to expose classic memory corruption vulnerabilities.

## Connection

```bash
ssh narnia0@narnia.labs.overthewire.org -p 2226
# Password: narnia0
# Binaries in /narnia/
```

## Concepts

| Level | Technique |
|-------|-----------|
| 0 | Stack buffer overflow — control EIP |
| 1 | Environment variable shellcode |
| 2 | Stack overflow with shellcode injection |
| 3 | Symlink + race condition |
| 4 | Large buffer overflow |
| 5 | Format string vulnerability |
| 6 | Format string — arbitrary write |
| 7 | Pointer corruption |
| 8 | Advanced format string |

## Useful Commands

```bash
# Inspect binary
file /narnia/narniaX
checksec /narnia/narniaX
objdump -d /narnia/narniaX | grep -A 20 main

# Generate pattern
python3 -c "print('A'*100)"
/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 200

# Find offset
gdb -q /narnia/narniaX
(gdb) run $(python3 -c "print('A'*100)")
(gdb) info registers
```
