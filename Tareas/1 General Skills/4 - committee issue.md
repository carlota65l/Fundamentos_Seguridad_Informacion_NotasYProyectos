## committee issue
## Descripcion

I accidentally wrote the flag down. Good thing I deleted it!You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/75/challenge.zip)
## Solucion
### solucion 1_ usando python

**recuperación de información eliminada dentro de un repositorio Git**, aplicando técnicas básicas de análisis forense en control de versiones.
 
```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/75/challenge.zip
--2026-02-19 01:16:56--  https://artifacts.picoctf.net/c_titan/75/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.170.131.33, 3.170.131.72, 3.170.131.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.170.131.33|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19196 (19K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip           100%[============================>]  18.75K  --.-KB/s    in 0.007s  

2026-02-19 01:16:56 (2.45 MB/s) - 'challenge.zip' saved [19196/19196]

BelovedCis-picoctf@webshell:~$ unzip challenge.zip
Archive:  challenge.zip
  
README.txt  __pycache__  challenge.zip  drop-in  serpentine.py
BelovedCis-picoctf@webshell:~$ BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/75/challenge.zip
-bash: BelovedCis-picoctf@webshell:~$: command not found
BelovedCis-picoctf@webshell:~$ --2026-02-19 01:16:56--  https://artifacts.picoctf.net/c_titan/75/challenge.zip
-bash: --2026-02-19: command not found
BelovedCis-picoctf@webshell:~$ Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.170.131.33, 3.170.131.72, 3.170.131.18, ...
-bash: syntax error near unexpected token `('
BelovedCis-picoctf@webshell:~$ Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.170.131.33|:443... connected.
-bash: syntax error near unexpected token `('
BelovedCis-picoctf@webshell:~$ HTTP request sent, awaiting response... 200 OK
-bash: HTTP: command not found
BelovedCis-picoctf@webshell:~$ Length: 19196 (19K) [application/octet-stream]
-bash: syntax error near unexpected token `('
BelovedCis-picoctf@webshell:~$ Saving to: 'challenge.zip'
-bash: Saving: command not found
BelovedCis-picoctf@webshell:~$ 
BelovedCis-picoctf@webshell:~$ challenge.zip           100%[============================>]  18.75K  --.-KB/s    in 0.007s  
-bash: challenge.zip: command not found
BelovedCis-picoctf@webshell:~$ 
BelovedCis-picoctf@webshell:~$ 2026-02-19 01:16:56 (2.45 MB/s) - 'challenge.zip' saved [19196/19196]
-bash: syntax error near unexpected token `('
BelovedCis-picoctf@webshell:~$ 
BelovedCis-picoctf@webshell:~$ BelovedCis-picoctf@webshell:~$ unzip challenge.zip
-bash: BelovedCis-picoctf@webshell:~$: command not found
BelovedCis-picoctf@webshell:~$ Archive:  challenge.zip
-bash: Archive:: command not found

-bash: README.txt: command not found
BelovedCis-picoctf@webshell:~$ BelovedCis-picoctf@webshell:~$ ls
-bash: BelovedCis-picoctf@webshell:~$: command not found
BelovedCis-picoctf@webshell:~$ README.txt  __pycache__  challenge.zip  drop-in  serpentine.py
-bash: README.txt: command not found
BelovedCis-picoctf@webshell:~$ BelovedCis-picoctf@webshell:~$ cd drop-in
-bash: BelovedCis-picoctf@webshell:~$: command not found
BelovedCis-picoctf@webshell:~$ git log
fatal: not a git repository (or any parent up to mount point /)
Stopping at filesystem boundary (GIT_DISCOVERY_ACROSS_FILESYSTEM not set).
BelovedCis-picoctf@webshell:~$ ls
README.txt  ]  __pycache__  challenge.zip  drop-in  serpentine.py
BelovedCis-picoctf@webshell:~$ cd drop-in
BelovedCis-picoctf@webshell:~/drop-in$ ls
message.txt
BelovedCis-picoctf@webshell:~/drop-in$ git status
On branch master
nothing to commit, working tree clean
BelovedCis-picoctf@webshell:~/drop-in$ git log
BelovedCis-picoctf@webshell:~/drop-in$ git log -p | grep pico
Author: picoCTF <ops@picoctf.com>
-picoCTF{s@n1t1z3_9539be6b}
Author: picoCTF <ops@picoctf.com>
+picoCTF{s@n1t1z3_9539be6b}
BelovedCis-picoctf@webshell:~/drop-in$ 
```

#### Procedimiento aplicado en el ejercicio

1. Se descargó el archivo comprimido.
2. Se extrajo el repositorio Git.
3. Se accedió al historial de commits.
4. Se visualizaron los cambios realizados.
5. Se identificó la flag eliminada.


Respuesta: picoCTF{s@n1t1z3_9539be6b}

## Notas

**Persistencia de datos en Git**

- Git no elimina definitivamente los archivos al borrarlos.
    
- Toda la información permanece almacenada en el historial de commits.
    
- Esto permite recuperar versiones anteriores incluso después de eliminaciones.

## Referencias
- Git — Sistema de control de versiones distribuido utilizado para gestionar cambios en proyectos.
    
- picoCTF — Plataforma educativa de retos de ciberseguridad orientados al aprendizaje práctico.