# FormulaOne

**Difficulty:** Hard | **Topics:** Advanced multi-stage exploitation — network programming, binary exploitation, crypto

Multi-stage exploitation wargame combining network-level interaction with advanced binary exploitation. Requires writing exploit code from scratch.

## Connection

```bash
ssh formulaone0@formulaone.labs.overthewire.org -p 2232
# Password: formulaone0
```

## Concepts

| Stage | Topics |
|-------|--------|
| Network | Custom protocol interaction via TCP/UDP |
| Crypto | Weak PRNG seeds, predictable tokens |
| Binary | Overflow + shellcode or ROP over network |
| Chain | Multi-step: network → leak → exploit |

## Approach

Each level typically requires:

1. Reverse the network protocol (Wireshark or strace on server)
2. Write a Python/C client to interact with the service
3. Identify the vulnerability (overflow, format string, UAF)
4. Develop exploit payload and deliver over socket

```python
from pwn import *

r = remote('formulaone.labs.overthewire.org', PORT)
# Interact with protocol
r.recvuntil(b'> ')
r.sendline(payload)
r.interactive()
```
