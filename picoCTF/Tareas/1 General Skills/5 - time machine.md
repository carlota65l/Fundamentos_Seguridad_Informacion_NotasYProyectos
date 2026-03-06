## time machine
## Descripcion

What was I last working on? I remember writing a note to help me remember...You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/66/challenge.zip)
## Solucion
### solucion 1_ usando python

**recuperar información almacenada en el historial de un repositorio Git**. La idea principal es que, aunque un archivo haya sido modificado o eliminado, Git conserva un registro completo de todos los cambios realizados.

En el ejercicio, se te entrega un archivo `.zip` que contiene una carpeta llamada `drop-in`, la cual incluye un directorio oculto `.git`. Esto indica que se trata de un repositorio Git.
 
```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/66/challenge.zip
--2026-02-19 01:33:07--  https://artifacts.picoctf.net/c_titan/66/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.170.131.18, 3.170.131.77, 3.170.131.33, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.170.131.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17740 (17K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip           100%[============================>]  17.32K  --.-KB/s    in 0.005s  

2026-02-19 01:33:07 (3.51 MB/s) - 'challenge.zip' saved [17740/17740]

BelovedCis-picoctf@webshell:~$ unzip challenge.zip
Archive:  challenge.zip
replace drop-in/message.txt? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: drop-in/message.txt     
replace drop-in/.git/description? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  
BelovedCis-picoctf@webshell:~$ ls
README.txt  __pycache__  challenge.zip  drop-in
BelovedCis-picoctf@webshell:~$ ls -a
.              .bash_logout  .local             .python_history  __pycache__
..             .bashrc       .ltdis.x86_64.txt  .ssh             challenge.zip
.bash_history  .lesshst      .profile           README.txt       drop-in
BelovedCis-picoctf@webshell:~$ git log
fatal: not a git repository (or any parent up to mount point /)
Stopping at filesystem boundary (GIT_DISCOVERY_ACROSS_FILESYSTEM not set).
BelovedCis-picoctf@webshell:~$ git log -p
fatal: not a git repository (or any parent up to mount point /)
Stopping at filesystem boundary (GIT_DISCOVERY_ACROSS_FILESYSTEM not set).
BelovedCis-picoctf@webshell:~$ cd drop-in
BelovedCis-picoctf@webshell:~/drop-in$ git log
BelovedCis-picoctf@webshell:~/drop-in$ 
```

1. **evisar el historial de commits**:
    
    `git log`
    
2. Allí aparece un commit que contiene directamente la flag:
    

`commit 3339c144a0c78dc2fbd3403d2fb37d3830be5d94 Author: picoCTF <ops@picoctf.com>  picoCTF{t1m3m@ch1n3_d3161c0f}`


Respuesta: picoCTF{t1m3m@ch1n3_d3161c0f}
## Notas

### Git guarda todo el historial

Git funciona como una **máquina del tiempo**:

- Cada commit es un “snapshot”
    
- Nunca se borran realmente los datos
    
- Incluso archivos eliminados pueden recuperarse
    

Por eso, en seguridad informática:
Un secreto subido a Git **no puede eliminarse completamente**.

## ⚠️ Importancia en ciberseguridad

Este tipo de vulnerabilidad ocurre en la vida real cuando:

- Se suben contraseñas a un repositorio
    
- Luego se eliminan creyendo que desaparecieron
    
- Pero siguen accesibles en el historial
    

Es una fuga de información muy común.
Consiste en investigar:

- Historial de commits
    
- Cambios en archivos
    
- Información eliminada

- Git almacena todos los cambios en el historial mediante commits.
    
- Cada commit tiene un identificador único llamado hash.
    
- La información eliminada de archivos puede recuperarse revisando el historial.
    
- El comando `git log` permite visualizar los commits.
    
- Los mensajes de commit también pueden contener información sensible.
    
- Un repositorio con carpeta `.git` contiene todo el historial completo.
## Referencias
- Documentación oficial de Git:  
    [https://git-scm.com/docs/git-log](https://git-scm.com/docs/git-log)
    
- Libro gratuito:  
    Pro Git — Scott Chacon & Ben Straub
    
- Guía de seguridad en repositorios:  
    OWASP — Secrets Management
    
- Plataforma del reto:  
    picoCTF