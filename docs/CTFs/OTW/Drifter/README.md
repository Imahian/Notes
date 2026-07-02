# Drifter

**Difficulty:** Hard | **Topics:** Advanced binary exploitation — ROP, heap, kernel modules, race conditions

One of the harder OverTheWire wargames. Combines multiple exploitation techniques including return-oriented programming and complex memory corruption chains.

## Connection

```bash
ssh drifter0@drifter.labs.overthewire.org -p 2230
# Password: drifter0
```

## Concepts

| Topic | Description |
|-------|-------------|
| ROP chains | Gadget chaining to bypass NX/DEP |
| ret2libc | Return to libc functions without shellcode |
| Heap corruption | Exploit malloc metadata for arbitrary write |
| Race conditions | TOCTOU in multi-threaded binaries |
| Kernel modules | Level 15 involves LKM exploitation |

## Recommended Prerequisites

- Solid x86/x64 assembly knowledge
- Comfortable with pwntools exploit development
- Understand ELF relocations and dynamic linking
- Complete Utumno and Maze first

## Tools

```bash
# Find ROP gadgets
ROPgadget --binary ./binary --rop
ropper -f ./binary

# ret2libc
python3 -c "from pwn import *; libc=ELF('/lib/i386-linux-gnu/libc.so.6'); print(hex(libc.symbols['system']))"
```
