### SSH Login Level 0→1
------

Primeramente necesitamos conectarnos al servidor de OverTheWire por el puerto 2220 con el usuario **bandit0** y contraseña **bandit0**

```bash
  ssh bandit0@bandit.labs.overthewire.org -p2220
```

Al tener acceso al servidor de Bandit, necesitamos listar el contenido que existe en la carpeta actual, habrá un fichero llamado readme

```bash
  ls -l
  
  readme
```

y visualizaremos el contenido del fichero 

```bash
  cat readme
```
