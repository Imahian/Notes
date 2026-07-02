# eCTHP

**eLearnSecurity Certified Threat Hunting Professional** — covers proactive threat detection using SIEM, EDR, log analysis, and MITRE ATT&CK-based hunting hypotheses.

## Exam Format

- **Duration:** 3 days
- **Format:** Hunt for adversary activity in a simulated environment
- **Deliverable:** Threat hunting report with findings and ATT&CK mappings

## Syllabus

| Domain | Topics |
|--------|--------|
| Threat Hunting Fundamentals | Hunt cycles, hypothesis-driven hunting, intelligence-led hunting |
| MITRE ATT&CK | Tactics, techniques, sub-techniques, procedure mapping |
| Windows Telemetry | Event IDs, Sysmon, Windows Defender logs, ETW |
| Linux Telemetry | Auditd, syslog, systemd journal, eBPF |
| SIEM Queries | Splunk SPL, Elastic KQL, hunting dashboards |
| Endpoint Detection | EDR alert correlation, process tree analysis |
| Network Detection | DNS anomalies, beaconing, C2 patterns in PCAP |
| Malware Hunting | LOLBAS, living-off-the-land techniques, fileless malware |

## Key Sysmon Event IDs

| Event ID | Description |
|----------|-------------|
| 1 | Process creation |
| 3 | Network connection |
| 7 | Image loaded (DLL) |
| 8 | CreateRemoteThread |
| 10 | ProcessAccess (LSASS dump) |
| 11 | FileCreate |
| 13 | Registry value set |
| 22 | DNS query |

## Splunk SPL Examples

```spl
# Detect LSASS credential dumping
index=wineventlog EventCode=10 TargetImage="*lsass.exe" | stats count by SourceImage,SourceProcessId

# Detect PowerShell download cradle
index=wineventlog EventCode=4688 CommandLine="*IEX*" OR CommandLine="*DownloadString*"

# Detect lateral movement via WMI
index=wineventlog EventCode=4688 NewProcessName="*wmiprvse.exe" | stats count by ParentProcessName
```
