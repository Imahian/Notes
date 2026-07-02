# Maze

**Difficulty:** Hard | **Topics:** Advanced binary exploitation, heap exploitation, ASLR bypass

Advanced exploitation wargame requiring deep understanding of memory layout, heap internals, and exploit mitigation bypass techniques.

## Connection

```bash
ssh maze0@maze.labs.overthewire.org -p 2225
# Password: maze0
```

## Concepts

| Topic | Description |
|-------|-------------|
| Heap exploitation | malloc/free internals, use-after-free, heap overflow |
| ASLR bypass | Info leak via format string or partial overwrite |
| ROP chains | Return-oriented programming when NX is enabled |
| GOT/PLT overwrite | Hijack function pointers via format string write |

## Recommended Prerequisites

- Complete Narnia and Behemoth first
- Understand glibc malloc internals (bins, chunks, metadata)
- Comfortable with GDB and pwntools

## Tools

```bash
# Heap analysis
gdb -q ./binary
(gdb) heap chunks
(gdb) heap bins

# pwntools
from pwn import *
context.arch = 'i386'
elf = ELF('./binary')
p = process('./binary')
```
