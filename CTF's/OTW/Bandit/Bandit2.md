### Hidden files 3 -> 4

En este nivel, tenemos información de que la contraseña para el siguiente nivel almacenado en un archivo llamado espacios en este nombre de archivo ubicado en el directorio home. Como el comando cat lee el nombre del archivo sólo hasta el espacio ya que considera el espacio como nulo '/0'. Si usamos directamente el comando cat, no será capaz de encontrar el archivo.

    ~# ssh bandit2@bandit.labs.overthewire.org -p 2220
    bandit2@bandit:~$ ls
    spaces in this filename
    bandit2@bandit:~$ cat 'spaces in this filename'
Consejos:
haga clic en el botón de tabulación después de escribir la primera palabra del comando o nombre de archivo, se rellenará automáticamente.
