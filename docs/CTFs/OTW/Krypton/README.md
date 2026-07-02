# Krypton

**Difficulty:** Beginner–Intermediate | **Topics:** Classical cryptography — Caesar, ROT13, Vigenère, substitution ciphers, frequency analysis

Seven levels of cryptographic challenges. Each password is encrypted with a classical cipher; you must break it to proceed.

## Connection

```bash
ssh krypton0@krypton.labs.overthewire.org -p 2231
# Password: krypton0
# Files in /krypton/kryptonN/
```

## Cipher Progression

| Level | Cipher | Break Method |
|-------|--------|--------------|
| 0 | Base64 | `base64 -d` |
| 1 | ROT13 | `tr 'A-Za-z' 'N-ZA-Mn-za-m'` |
| 2 | Caesar | Brute force all 25 shifts |
| 3 | Simple substitution | Frequency analysis |
| 4 | Vigenère (known key) | Decrypt with key |
| 5 | Vigenère (unknown key) | Index of coincidence → key length → frequency |
| 6 | Stream cipher (weak PRNG) | Known plaintext attack |

## Useful Tools

```bash
# Caesar brute force
for i in $(seq 1 25); do cat cipher | tr 'A-Z' $(python3 -c "import string; a=string.ascii_uppercase; print(a[$i:]+a[:$i])"); done

# Frequency analysis
cat cipher | tr -d ' \n' | fold -w1 | sort | uniq -c | sort -rn

# Python Vigenère
python3 -c "
key='KEY'; ct='CIPHERTEXT'
pt=''.join(chr((ord(c)-ord(key[i%len(key)]))%26+65) for i,c in enumerate(ct))
print(pt)"
```
