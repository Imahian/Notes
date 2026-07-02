# HTTrack

Open-source website crawler and offline browser. Downloads complete websites — HTML, CSS, JS, images — for offline analysis.

**GitHub:** https://github.com/xroche/httrack  
**Official site:** https://www.httrack.com

## Installation

```bash
sudo apt install httrack
```

## Basic usage

```bash
# Clone a full website
httrack "https://example.com" -O "/path/to/output/"

# Limit crawl depth
httrack "https://example.com" -O "/path/to/output/" -r2

# Exclude specific file types
httrack "https://example.com" -O "/path/to/output/" -*.png -*.jpg

# Mirror with no external links
httrack "https://example.com" -O "/path/to/output/" -%e0
```

## Key options

| Option | Description |
|--------|-------------|
| `-O <dir>` | Output directory |
| `-r<n>` | Max crawl depth (default: unlimited) |
| `-*.ext` | Exclude file types |
| `+*.ext` | Include only specific file types |
| `-%e0` | Don't follow external links |
| `-c<n>` | Max simultaneous connections |
| `--mirror` | Full mirror mode |

## What it downloads

- HTML pages and internal links
- CSS stylesheets and JS files
- Images and multimedia
- Documents (PDF, etc.) if linked

## Use cases in security

- **Web application recon** — map directory structure, find hidden endpoints, JS file analysis
- **Technology fingerprinting** — inspect frontend frameworks, comment leaks, version strings in source
- **Historical comparison** — clone now, compare later to detect changes
- **Offline analysis** — examine source without repeated server requests

## Complementary tools

| Tool | Use |
|------|-----|
| `wget -r` | Simpler recursive web download |
| Burp Suite | Intercept/analyze live HTTP traffic |
| Wayback Machine Downloader | Download historical site snapshots |
| `curl` | Single-page download with full headers |
