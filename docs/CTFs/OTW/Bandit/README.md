# Bandit

**Difficulty:** Beginner | **Topics:** Linux CLI, SSH, file permissions, scripting, encoding

The entry point for OverTheWire. Teaches essential Linux command-line skills used in every other wargame and real pentest.

## Connection

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
# Password: bandit0
# Next level password stored somewhere on the system
```

Each level's password is stored in `/etc/bandit_pass/banditN` — only readable by that user.

## Concepts by Level

| Levels | Concepts |
|--------|----------|
| 0–5 | SSH, ls, cat, find, file, strings |
| 6–10 | find flags, file ownership, hidden files, base64 |
| 11–15 | rot13, xxd, gzip/bzip2/tar, nc |
| 16–20 | SSL/TLS, nmap, setuid, cron |
| 21–27 | shell scripts, git, diff |
| 28–34 | git branches, tags, commits, rebasing |

## Key Commands

```bash
find / -user banditN -readable 2>/dev/null
strings <file>
base64 -d <file>
xxd <file> | head
file <file>
nc localhost <port>
openssl s_client -connect localhost:<port>
```

## Writeups

- [Level 0](<Level 0/README.md>)
- [Level 1](<Level 1/README.md>)
