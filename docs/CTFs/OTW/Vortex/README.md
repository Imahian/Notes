# Vortex

**Difficulty:** Hard | **Topics:** Network programming, binary exploitation, C, socket programming

Challenges require writing custom network clients in C or Python before exploitation can begin. Combines network programming with binary exploitation.

## Connection

```bash
ssh vortex0@vortex.labs.overthewire.org -p 2228
# Password: vortex0
```

## Concepts

| Levels | Topics |
|--------|--------|
| 0 | TCP client — receive numbers, send computed value |
| 1 | Fork bomb mitigation, process management |
| 2–4 | Stack overflows with network vector |
| 5+ | ROP chains, network shellcode delivery |

## Network Client Template (Python)

```python
import socket, struct

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('vortex.labs.overthewire.org', 5842))

# Read 4 unsigned ints, sum them, send back
total = 0
for _ in range(4):
    data = s.recv(4)
    total += struct.unpack('<I', data)[0]

s.send(struct.pack('<I', total & 0xFFFFFFFF))
print(s.recv(1024))
```
