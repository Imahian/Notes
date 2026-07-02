# CVEs

CVE research, proof-of-concept analysis, and exploitation notes for publicly disclosed vulnerabilities.

## Format

Each CVE entry includes:

- **Affected software** and vulnerable versions
- **Vulnerability type** (RCE, LFI, SQLi, privilege escalation, etc.)
- **CVSS score** and severity
- **Root cause** — the actual bug in the code
- **Exploitation** — PoC commands or scripts
- **Patch/mitigation**

## Severity Reference

| CVSS | Severity | Impact |
|------|----------|--------|
| 9.0–10.0 | Critical | Remote code execution, no auth |
| 7.0–8.9 | High | Auth bypass, significant data exposure |
| 4.0–6.9 | Medium | Requires interaction or specific conditions |
| 0.1–3.9 | Low | Limited impact |

## Research Sources

- [NVD](https://nvd.nist.gov) — National Vulnerability Database
- [Exploit-DB](https://exploit-db.com) — Public exploits
- [GitHub Security Advisories](https://github.com/advisories) — OSS vulns
- [VulnHub CVEs](https://www.vulnhub.com) — Practical exploitation
- [Packet Storm](https://packetstormsecurity.com) — PoCs and advisories

## Exploitation Template

```bash
# Search for existing exploits
searchsploit <software> <version>
searchsploit -m <exploit-id>

# CVE lookup
curl "https://cve.circl.lu/api/cve/CVE-YYYY-NNNNN" | jq .

# Run PoC
python3 exploit.py --target <IP> --port <PORT>
```
