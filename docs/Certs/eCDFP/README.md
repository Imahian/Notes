# eCDFP

**eLearnSecurity Certified Digital Forensics Professional** — covers disk, memory, network, and mobile forensics with emphasis on proper evidence handling and reporting.

## Exam Format

- **Duration:** 3 days
- **Format:** Analyze forensic images and answer investigative questions
- **Deliverable:** Forensic investigation report

## Syllabus

| Domain | Topics |
|--------|--------|
| Forensics Fundamentals | Chain of custody, write blockers, hashing, legal considerations |
| Disk Forensics | File system analysis (NTFS, ext4, FAT32), deleted file recovery, timeline |
| Windows Artifacts | Registry, prefetch, LNK, Jump Lists, browser history, event logs |
| Linux Artifacts | /var/log, bash history, cron, systemd, syslog |
| Memory Forensics | RAM acquisition, process analysis, network connections, injected code |
| Network Forensics | PCAP reconstruction, email headers, protocol analysis |
| Mobile Forensics | Android/iOS acquisition, SQLite databases, app artifacts |
| Report Writing | Executive summary, technical findings, evidence chain |

## Tools

```bash
# Disk imaging
dd if=/dev/sdb of=image.dd bs=4M status=progress
dcfldd if=/dev/sdb of=image.dd hash=sha256 hashlog=hash.txt

# Hash verification
sha256sum image.dd

# Autopsy / Sleuth Kit
mmls image.dd                    # partition table
fls -r -m / image.dd -o <offset> # file listing
icat image.dd -o <offset> <inode> > recovered_file

# Volatility
vol.py -f memory.dmp windows.info
vol.py -f memory.dmp windows.pstree
vol.py -f memory.dmp windows.filescan | grep -i ".exe"
```
