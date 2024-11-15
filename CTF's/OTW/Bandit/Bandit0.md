### SSH Login Level 0→1

Primeramente necesitamos conectarnos al servidor de OverTheWire por el puerto 2220 con el usuario **bandit0** y contraseña **bandit0**

```bash
  bandit0@bandit:~$ ssh bandit0@bandit.labs.overthewire.org -p2220
```

Al tener acceso al servidor de Bandit, necesitamos listar el contenido que existe en la carpeta actual, habrá un fichero llamado readme

```bash
  bandit0@bandit:~$ ls -l
  
  readme
```

y visualizaremos el contenido del fichero 

```bash
  cat readme
```

## Explicaciones de los comandos

**ls -l** Listar el contenido del directorio utilizando un formato de listado largo

**cat** Concatenar archivos e imprimir en la salida estándar
