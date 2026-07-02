# eCIR

**eLearnSecurity Certified Incident Responder** — covers the full incident response lifecycle from detection to containment, eradication, and recovery.

## Exam Format

- **Duration:** 3 days
- **Format:** Analyze a simulated compromise — identify attacker TTPs and timeline
- **Deliverable:** Incident response report

## Syllabus

| Domain | Topics |
|--------|--------|
| IR Fundamentals | PICERL framework, chain of custody, evidence handling |
| Windows Forensics | Event logs, registry hives, prefetch, LNK files, $MFT |
| Linux Forensics | Auth logs, bash history, cron, syslog, auditd |
| Memory Forensics | Volatility — process injection, network connections, malware |
| Network Forensics | PCAP analysis, C2 identification, lateral movement detection |
| Malware Analysis | Static/dynamic analysis, sandbox detonation, IOC extraction |
| Threat Intelligence | MITRE ATT&CK mapping, TTPs, IOCs, threat actors |

## Key Commands

```bash
# Windows event log analysis
Get-WinEvent -LogName Security | Where-Object {$_.Id -eq 4624} | Select-Object TimeCreated,Message

# Volatility (memory)
vol.py -f memory.raw imageinfo
vol.py -f memory.raw --profile=Win10x64 pstree
vol.py -f memory.raw --profile=Win10x64 netscan
vol.py -f memory.raw --profile=Win10x64 malfind

# PCAP with tshark
tshark -r capture.pcap -Y "http.request" -T fields -e ip.src -e http.host -e http.request.uri
```

## Tools

`volatility` `autopsy` `wireshark` `tshark` `yara` `velociraptor` `Splunk`
