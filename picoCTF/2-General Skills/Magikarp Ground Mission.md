## Magikarp Ground Mission
## Descripcion
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin.

Login via `ssh` as `ctf-player` with the password, `8c606eb1` on the host `wily-courier.picoctf.net` and port `62053`.
## Solucion
### solucion 1_ usando python



 
```bash
BelovedCis-picoctf@webshell:~$ ssh ctf-player@wily-courier.picoctf.net -p 62053
ctf-player@wily-courier.picoctf.net's password: 
Welcome to Ubuntu 18.04.6 LTS (GNU/Linux 6.14.0-1012-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Last login: Thu Feb 12 01:30:33 2026 from 127.0.0.1
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
ctf-player@pico-chall$ cat 1of3.flag.txt
picoCTF{xxsh_
ctf-player@pico-chall$ cat instructions-to-2of3.txt
Next, go to the root of all things, more succinctly `/`
ctf-player@pico-chall$ cd /
ctf-player@pico-chall$ ls
2of3.flag.txt  challenge  home                      lib64  opt   run   sys  var
bin            dev        instructions-to-3of3.txt  media  proc  sbin  tmp
boot           etc        lib                       mnt    root  srv   usr
ctf-player@pico-chall$ cat 2of3.flag.txt
0ut_0f_//4t3r_
ctf-player@pico-chall$ cat instructions-to-3of3.txt
Lastly, ctf-player, go home... more succinctly `~`
ctf-player@pico-chall$ cd ~
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat -A 3of3.flag.txt
0b24fc4f}ctf-player@pico-chall$ 
```

Respuesta: picoCTF{xxsh_0ut_0f_//4t3r_0b24fc4f}

## Notas
El desafío tiene como finalidad evaluar conocimientos básicos sobre:

- Conexión remota mediante SSH.
    
- Navegación en el sistema de archivos Linux.
    
- Lectura de archivos desde la terminal.
    
- Comprensión de rutas absolutas y relativas.
    
- Uso del directorio raíz (`/`) y el directorio home (`~`).


### Conexión Remota con SSH

El protocolo **SSH (Secure Shell)** permite conectarse de manera segura a un servidor remoto mediante autenticación.
### Comando utilizado:

`ssh ctf-player@wily-courier.picoctf.net -p 62053`
### Componentes:

- `ssh` → Cliente de conexión remota.
    
- `ctf-player` → Usuario.
    
- `@host` → Servidor remoto.
    
- `-p` → Puerto personalizado.
---

### Navegación en el Sistema de Archivos

### Comandos utilizados:

|Comando|Función|
|---|---|
|`ls`|Lista archivos y directorios|
|`cd`|Cambia de directorio|
|`cd /`|Ir al directorio raíz|
|`cd ~` o `cd`|Volver al directorio home|
|`pwd`|Muestra la ruta actual|
|`cat`|Muestra el contenido de un archivo|


### Directorio Raíz `/`

Es el nivel más alto del sistema de archivos en Linux.  
Contiene carpetas fundamentales como:

- `/bin`
    
- `/etc`
    
- `/home`
    
- `/root`
    
- `/usr`
    

###  Directorio Home `~`

Es el directorio personal del usuario actual.  
En este caso:

`/home/ctf-player`

El símbolo `~` es un atajo hacia esa ruta.

###  Lectura de Archivos

Se utilizó el comando:

`cat archivo.txt`

En el tercer fragmento fue necesario utilizar:

`cat -A archivo.txt`

Esto permite visualizar:

- Caracteres invisibles
    
- Saltos de línea
    
- Símbolos especiales
    

### Ensamblaje del Flag

El reto dividió el flag en tres partes ubicadas en diferentes directorios:

1. Home del usuario
    
2. Directorio raíz `/`
    
3. Nuevamente el home
    

Se unieron los fragmentos para formar el flag completo.

### Competencias Evaluadas

- Uso básico de Linux
    
- Comprensión de jerarquía de directorios
    
- Interpretación de instrucciones en archivos
    
- Manejo de rutas absolutas y relativas
    
- Uso de comandos esenciales en CTF

## Referencias
- - OpenSSH Manual  
    [https://man.openbsd.org/ssh](https://man.openbsd.org/ssh)
    
- GNU Bash Reference Manual  
    [https://www.gnu.org/software/bash/manual/](https://www.gnu.org/software/bash/manual/)
    
- Linux Filesystem Hierarchy Standard (FHS)  
    [https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
    
- Manual del comando `ls`  
    [https://man7.org/linux/man-pages/man1/ls.1.html](https://man7.org/linux/man-pages/man1/ls.1.html)
    
- Manual del comando `cat`  
    [https://man7.org/linux/man-pages/man1/cat.1.html](https://man7.org/linux/man-pages/man1/cat.1.html)
    
- picoCTF Official Site  
    [https://picoctf.org](https://picoctf.org)