# Utumno

**Difficulty:** Intermediate–Hard | **Topics:** Binary exploitation — buffer overflows, format strings, shellcode, GOT overwrites

Harder binary exploitation wargame. Requires understanding of ELF internals, GOT/PLT, and exploit mitigation awareness.

## Connection

```bash
ssh utumno0@utumno.labs.overthewire.org -p 2227
# Password: utumno0
# Binaries in /utumno/
```

## Concepts

| Level | Technique |
|-------|-----------|
| 0 | Environment variable expansion abuse |
| 1 | Buffer overflow — no NUL byte restriction |
| 2 | Argv overflow — shellcode in argument |
| 3 | Format string — stack leak |
| 4 | Off-by-one heap overflow |
| 5 | Format string → GOT overwrite |
| 6 | Complex control flow corruption |
| 7 | Multi-stage exploitation |

## Tools

```bash
# GDB with PEDA/pwndbg
gdb -q /utumno/utumnoX
pwndbg> checksec
pwndbg> disass main
pwndbg> pattern create 200
pwndbg> run $(python3 -c "print('A'*200)")

# Find GOT entries
objdump -R /utumno/utumnoX

# pwntools exploit template
from pwn import *
p = process('/utumno/utumnoX')
```
