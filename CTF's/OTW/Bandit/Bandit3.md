### Hidden Files 3 → 4

La contraseña para el siguiente nivel se almacena en un archivo oculto en el directorio inhere . Como [ls](https://www.tecmint.com/15-basic-ls-command-examples-in-linux/) sin comando de opción no mostrará archivos ocultos. Entonces necesitamos un comando para mostrar archivos ocultos en ese directorio.

    ~# ssh bandit3@bandit.labs.overthewire.org -p 2220bandit3@bandit:~$ ls
    inhere
    bandit3@bandit:~$ cd inhere
    bandit3@bandit:~/inhere$ ls -al
    total 12
    drwxr-xr-x 2 root    root    4096 Oct 16  2018 .
    drwxr-xr-x 3 root    root    4096 Oct 16  2018 ..
    -rw-r----- 1 bandit4 bandit3   33 Oct 16  2018 .hidden
    bandit3@bandit:~/inhere$ cat .hidden

## Explicación del comando
  cd  → Cambiar el directorio de trabajo del shell. 
  ls -al  → Comando de opción  usado  para mostrar todos los archivos en el directorio y  usado  para mostrar archivos en formato de lista larga. 
      
