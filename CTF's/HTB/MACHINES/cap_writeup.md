# Cap

<div align='center'>
  <img src='Screenshot_20241214_154049.png' width='400' alt='Machine Image'>
</div>

## Reco

escaneo de puertos [nmap](https://nmap.org)

```bash
 sudo nmap -sS --open --min-rate 5000 -n -Pn -vvv -oG allPorts 10.10.152.174
```

<div align='center'>
  <img src='Screenshot_20241128_031108.png' width='600' alt='Reco'>
</div>

## Servicios en puertos

escaneo de servicios

```bash
 nmap -sV -p21,53,88,135,139,389,445,464,593,636,3268,3269,5985 -oN targeted 10.10.11.42
```

<div align='center'>
  <img src='Screenshot_20250126_000211.png' width='600' alt='Servicios en puertos'>
</div>


```bash
Flag: fefwefw*******
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
