# OverTheWire

[overthewire.org/wargames](https://overthewire.org/wargames) — SSH-based wargames covering Linux fundamentals, binary exploitation, web security, and cryptography.

## Wargames

| Wargame | Difficulty | Topics |
|---------|------------|--------|
| [Bandit](Bandit/) | Beginner | Linux CLI, SSH, file permissions, scripting |
| [Leviathan](Leviathan/) | Beginner | SUID, file permissions, ltrace/strace |
| [Natas](Natas/) | Beginner–Intermediate | Web: PHP, SQLi, XSS, file inclusion, crypto |
| [Krypton](Krypton/) | Beginner–Intermediate | Classical cryptography, ciphers |
| [Narnia](Narnia/) | Intermediate | C, buffer overflows, shellcode, SUID |
| [Behemoth](Behemoth/) | Intermediate | Buffer overflows, format strings, symlinks |
| [Utumno](Utumno/) | Intermediate–Hard | Binary exploitation, shellcoding |
| [Maze](Maze/) | Hard | Advanced binary exploitation |
| [Vortex](Vortex/) | Hard | Network programming, binary exploitation |
| [Manpage](Manpage/) | Hard | GTFOBins-style exploitation via man pages |
| [Drifter](Drifter/) | Hard | Advanced exploitation chain |
| [FormulaOne](FormulaOne/) | Hard | Advanced multi-stage exploitation |

## Connection Template

```bash
ssh bandit<level>@bandit.labs.overthewire.org -p 2220
# Password from previous level
```

Each wargame has its own hostname and port. Check each section for connection details.
