# VulnHub

[vulnhub.com](https://vulnhub.com) — Collection of intentionally vulnerable VMs for offline penetration testing practice. Download, import into VirtualBox or VMware, and attack from your local network.

## Setup

```bash
# 1. Download .ova or .vmdk from vulnhub.com
# 2. Import into VirtualBox: File → Import Appliance
# 3. Set network adapter to Host-Only or NAT (match your Kali)
# 4. Boot VM and discover IP:

sudo arp-scan -l
# or
sudo netdiscover -r 192.168.56.0/24
```

## Characteristics

- **No hints or guidance** — fully black-box
- **Varies widely** in quality and realism
- **Older CVEs** often required — snapshot VMs before exploitation
- **Boot-to-root** format: foothold → escalate → read `/root/flag.txt`

## Recommended Series

| Series | Focus |
|--------|-------|
| Mr. Robot | Web, Linux, CTF themed |
| Kioptrix | Classic Linux exploitation |
| DC series | Varied, beginner to intermediate |
| HarryPotter | Chain of machines |
| Symfonos | Active Directory simulation |
