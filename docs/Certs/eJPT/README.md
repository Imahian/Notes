# eJPT — Junior Penetration Tester

eLearnSecurity / INE certification covering networking fundamentals, host & network pentesting, and web application security.

## Module 1: Networking Fundamentals

### Core Terminology

| Term | Description |
|------|-------------|
| Network | Set of interconnected devices sharing resources. LAN (local) or WAN (wide area). |
| Node | Any device on the network: computer, router, switch. |
| Protocol | Rule set governing data transmission. Examples: TCP/IP, HTTP, FTP. |
| Bandwidth | Max data throughput, measured in bits per second (bps). |
| Latency | Time for a packet to travel from source to destination. Lower = faster. |
| Packet | Basic data unit. Contains payload + headers (source/destination addresses). |
| Firewall | Device or software controlling inbound/outbound traffic via security rules. |

### OSI Model (7 Layers)

| # | Layer | Function | Examples |
|---|-------|----------|---------|
| 7 | Application | User-facing services | HTTP, FTP, SMTP, DNS |
| 6 | Presentation | Data format translation, encryption | SSL/TLS |
| 5 | Session | Connection management between apps | RPC |
| 4 | Transport | Reliable end-to-end delivery | TCP, UDP |
| 3 | Network | Routing between networks | IP, ICMP |
| 2 | Data Link | Direct node-to-node transfer | MAC, Ethernet |
| 1 | Physical | Hardware transmission (cables, signals) | Ethernet cables, USB |

### TCP/IP Model (4 Layers)

| # | Layer | OSI Equivalent | Examples |
|---|-------|---------------|---------|
| 4 | Application | App + Presentation + Session | HTTP, FTP, DNS |
| 3 | Transport | Transport | TCP, UDP |
| 2 | Internet | Network | IP, ICMP |
| 1 | Network Access | Data Link + Physical | Ethernet, Wi-Fi |

### Subnetting & CIDR

- **IP Address**: Unique device identifier. IPv4 (`192.168.1.1`) or IPv6 (`2001:db8::1`).
- **Subnet Mask**: Separates network vs host portion of an IP. Common: `255.255.255.0`.
- **CIDR**: Compact notation — `192.168.1.0/24` means 24 bits for network, 8 for hosts.

#### CIDR Quick Reference

| CIDR | Subnet Mask | Hosts (usable) |
|------|-------------|----------------|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /16 | 255.255.0.0 | 65,534 |
| /8 | 255.0.0.0 | 16,777,214 |

**Example:** `192.168.1.0/24`
- Network: `192.168.1.0`, Broadcast: `192.168.1.255`
- Usable hosts: `192.168.1.1` – `192.168.1.254` (254 addresses)

#### Subnetting benefits
- **Security** — isolate network segments, limit blast radius
- **Efficiency** — avoid IP waste on large flat networks
- **Traffic reduction** — local traffic stays within subnet
