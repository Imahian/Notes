# Leviathan

**Difficulty:** Beginner | **Topics:** SUID binaries, ltrace, strace, file permissions, symlinks

Short wargame (8 levels) focusing on abusing setuid programs and observing binary behavior with dynamic analysis tools.

## Connection

```bash
ssh leviathan0@leviathan.labs.overthewire.org -p 2223
# Password: leviathan0
```

## Concepts

| Tool | Use |
|------|-----|
| `ltrace` | Trace library calls — reveals strcmp arguments, file paths |
| `strace` | Trace system calls — reveals open(), read(), access() |
| `strings` | Extract readable strings from binaries |
| symlinks | Abuse `access()` TOCTOU race or mislead file open paths |

## Pattern

Most levels involve a SUID binary owned by the next user. The workflow:

```bash
ls -la /usr/bin/leviathan*   # find suid binaries
ltrace ./binary              # observe strcmp(input, password)
strace ./binary 2>&1 | grep open  # observe file access
```
