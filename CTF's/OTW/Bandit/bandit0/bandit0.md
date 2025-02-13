# Bandit0

<div align='center'>
  <img src='machine_image.png' width='400' alt='Machine Image'>
</div>

## Recon

Scaning open ports with en [nmap](https://nmap.org)

```bash
 sudo nmap -p- -sS --min-rate 5000 -Pn -vvv -oG allPorts 10.10.11.3
```

<div align='center'>
  <img src='allPorts.png' width='600' alt='Recon'>
</div>

## services

Services running on ports

```bash
 nmap -sCV -p443,53,445,139,80,5985,3269,49456,49473,49436,9389,3268,49664,49449,464,389,49669,636,88,593 -oN targeted 10.10.11.3
```

<div align='center'>
  <img src='services_ports.png' width='600' alt='services'>
</div>


```bash
Flag: gdfjhdsgjfgd*************
```

## Siguenos

<div align='center'>
  <p>Thanks for reading! Follow me on my socials:</p>
  <a href='https://x.com/@imahian'><img src='https://www.vectorlogo.zone/logos/x/x-icon.svg' alt='X' width='40'></a>
  <a href='https://discord.gg/dbesG8EX'><img src='https://www.vectorlogo.zone/logos/discord/discord-icon.svg' alt='Discord' width='40'></a>
  <a href='https://youtube.com/@imahian'><img src='https://www.vectorlogo.zone/logos/youtube/youtube-icon.svg' alt='YouTube' width='40'></a>
  <a href='https://twitch.tv/imahian'><img src='https://www.vectorlogo.zone/logos/twitch/twitch-icon.svg' alt='Twitch' width='40'></a>
</div>

---
