### Read file 1 → 2

En este nivel, debemos capturar la contraseña para el siguiente nivel almacenada en un archivo llamado (-) ubicado en el directorio de inicio. Pero no es simplemente como antes, no podemos leer el (-) con comando de gato común. Cuando cat ve la cuerda - como nombre de archivo, lo trata como sinónimo de stdin. 

    bandit1@bandit:~$ ls 
    -
    bandit1@bandit:~$ cat ./-
    {Aquí verías la clave para el siguiente nivel}


## Explicación del comando 
./-  → El prefijo del nombre del archivo con una ruta utilizada para modificar la cadena del nombre del archivo para que el comando cat haga referencia a un archivo llamado  -  .    
