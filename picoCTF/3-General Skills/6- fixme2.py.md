##  fixme2.py
## Descripcion

Fix the syntax error in the Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/6/fixme2.py)
## Solucion
### solucion 1_ usando python

dentificar y corregir un error de sintaxis en un script escrito en el lenguaje de programación Python, proporcionado por la plataforma picoCTF. El objetivo es analizar el código fuente, localizar el error y corregirlo para permitir la ejecución correcta del programa y obtener la flag.

El archivo proporcionado, denominado **fixme2.py**, contiene un programa que utiliza una función de cifrado basada en la operación XOR para descifrar una cadena codificada que corresponde a la flag. Sin embargo, el script presenta un error en el uso del operador de comparación dentro de una estructura condicional, lo que provoca un error de sintaxis al momento de ejecutar el programa.

Para resolver el ejercicio, fue necesario analizar el código, identificar el uso incorrecto del operador de asignación (=) en lugar del operador de comparación (==), corregir el error y ejecutar nuevamente el script para obtener la flag.
 
```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/6/fixme2.py
--2026-02-16 18:38:32--  https://artifacts.picoctf.net/c/6/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.43, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: 'fixme2.py'

fixme2.py               100%[=============================>]   1.00K  --.-KB/s    in 0s      

2026-02-16 18:38:32 (58.4 MB/s) - 'fixme2.py' saved [1029/1029]

BelovedCis-picoctf@webshell:~$ python3 fixme2.py
  File "/home/BelovedCis-picoctf/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
BelovedCis-picoctf@webshell:~$ cat fixme2.py

import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x58) + chr(0x18) + chr(0x11) + chr(0x41) + chr(0x09) + chr(0x5f) + chr(0x1f) + chr(0x10) + chr(0x3b) + chr(0x1b) + chr(0x55) + chr(0x1a) + chr(0x34) + chr(0x5d) + chr(0x51) + chr(0x40) + chr(0x54) + chr(0x09) + chr(0x05) + chr(0x04) + chr(0x57) + chr(0x1b) + chr(0x11) + chr(0x31) + chr(0x0d) + chr(0x5f) + chr(0x05) + chr(0x40) + chr(0x04) + chr(0x0b) + chr(0x0d) + chr(0x0a) + chr(0x19)

  
flag = str_xor(flag_enc, 'enkidu')

# Check that flag is not empty
if flag = "":
  print('String XOR encountered a problem, quitting.')
else:
  print('That is correct! Here\'s your flag: ' + flag)


BelovedCis-picoctf@webshell:~$ nano fixme2.py
BelovedCis-picoctf@webshell:~$ python3 fixme2.py
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}

## Notas

- Python distingue entre el operador de asignación (=) y el operador de comparación (==).
    
- El operador (=) se utiliza para asignar valores a una variable.
    
- El operador (==) se utiliza para comparar dos valores.
    
- El uso incorrecto del operador provoca errores de sintaxis.
    
- La estructura condicional if permite ejecutar código basado en una condición.
    
- La función utilizada en el script emplea el operador XOR, común en técnicas de cifrado.
    
- El comando nano permite editar archivos desde la terminal.
    
- El comando python3 permite ejecutar scripts en Python.
    

Importancia en ciberseguridad:

Este ejercicio permite desarrollar habilidades como:

- Análisis de código fuente
    
- Identificación de errores en programas
    
- Comprensión de algoritmos de cifrado básicos
    
- Corrección de errores de programación
    
- Ejecución de scripts en entornos Linux
## Referencias
picoCTF. Plataforma educativa de ciberseguridad.
Python Software Foundation. Documentación oficial del lenguaje Python. [https://www.python.org](https://www.python.org)

Shotts, W. E. (2019). The Linux Command Line. No Starch Press.

Documentación oficial de Python. Operadores y estructuras condicionales.