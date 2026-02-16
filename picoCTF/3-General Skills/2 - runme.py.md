## runme.py
## Descripcion

Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell.[Download runme.py Python script](https://artifacts.picoctf.net/c/34/runme.py)

## Solucion

Al ejecutarlo correctamente, el script muestra en pantalla la flag, que confirma que el ejercicio se ha realizado correctamente.
### solucion 1_ usando python


 
```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/34/runme.py
--2026-02-16 18:07:31--  https://artifacts.picoctf.net/c/34/runme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.16, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270 [application/octet-stream]
Saving to: 'runme.py'

runme.py                100%[=============================>]     270  --.-KB/s    in 0s      

2026-02-16 18:07:31 (101 MB/s) - 'runme.py' saved [270/270]

BelovedCis-picoctf@webshell:~$ ls
Addadshashanammu      README.txt     big-zip-files.zip  files      runme.py
Addadshashanammu.zip  big-zip-files  enc_flag           files.zip
BelovedCis-picoctf@webshell:~$ python3 runme.py
picoCTF{run_s4n1ty_run}
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{run_s4n1ty_run}

## Notas

- Python es un lenguaje de programación interpretado, lo que significa que el código se ejecuta mediante un intérprete sin necesidad de compilación previa.
    
- El comando **wget** es una herramienta que permite descargar archivos desde internet mediante una URL.
    
- La extensión **.py** identifica archivos que contienen código fuente en Python.
    
- El comando **python3** se utiliza para ejecutar scripts escritos en la versión 3 de Python.
    
- Los scripts pueden utilizarse para automatizar tareas, procesar datos o ejecutar instrucciones específicas en el sistema.
    

Importancia en ciberseguridad:

El uso de scripts es fundamental en ciberseguridad porque permite:

- Automatizar análisis de sistemas
    
- Ejecutar herramientas de seguridad
    
- Analizar vulnerabilidades
    
- Recuperar información de sistemas remotos
    
- Realizar pruebas de penetración
    

Este ejercicio ayuda a desarrollar habilidades básicas necesarias para trabajar en entornos de seguridad informática.
## Referencias

picoCTF. Plataforma educativa de prácticas de ciberseguridad.

Python Software Foundation. (s.f.). Documentación oficial de Python. Python.org

Raymond, E. S. (2003). The Art of Unix Programming. Addison-Wesley.

Shotts, W. E. (2019). The Linux Command Line. No Starch Press.

Documentación oficial de Linux. Comandos wget, python3 y ls.