# Behemoth

**Difficulty:** Intermediate | **Topics:** Buffer overflows, format strings, symbolic links, environment variables, command injection

Eight levels of binary and filesystem exploitation. Programs have SUID bits set — exploiting them grants access to the next level's credentials.

## Connection

```bash
ssh behemoth0@behemoth.labs.overthewire.org -p 2221
# Password: behemoth0
# Binaries in /behemoth/
# Passwords in /etc/behemoth_pass/
```

## Concepts

| Level | Technique |
|-------|-----------|
| 0 | Hardcoded password — ltrace reveals strcmp |
| 1 | Buffer overflow — EIP control |
| 2 | Symlink attack — predictable temp file |
| 3 | Format string — info leak |
| 4 | Buffer overflow with environment variable shellcode |
| 5 | Network socket + hardcoded logic |
| 6 | Shellcode in environment, ltrace bypass |
| 7 | Format string — arbitrary write to GOT |

## Techniques

```bash
# Observe binary behavior
ltrace /behemoth/behemoth0
strace /behemoth/behemoth0 2>&1 | grep -E "open|read|write"

# Symlink attack
ln -s /etc/behemoth_pass/behemothN /tmp/predictable_tempfile

# Environment shellcode
export SHELLCODE=$(python3 -c "print('\x90'*100 + shellcode)")
```
