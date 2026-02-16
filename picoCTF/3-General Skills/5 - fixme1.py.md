##  fixme1.py
## Descripcion

Fix the syntax error in this Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/25/fixme1.py)

## Solucion
### solucion 1_ usando python

analizar y corregir un error de sintaxis en un script escrito en el lenguaje de programación Python, proporcionado por la plataforma picoCTF. El objetivo principal es identificar y solucionar un error de indentación que impide la ejecución correcta del programa, permitiendo así obtener la flag.

El archivo proporcionado, denominado **fixme1.py**, contiene código que utiliza una función de cifrado basada en la operación XOR para descifrar una cadena que corresponde a la flag. Sin embargo, el script presenta un error de indentación en la instrucción de impresión, lo que provoca que el intérprete de Python genere un mensaje de error y detenga la ejecución del programa.

Para resolver el ejercicio, fue necesario analizar el código, identificar la línea con la indentación incorrecta y corregirla para permitir la ejecución correcta del script.

```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/25/fixme1.py
--2026-02-16 18:30:09--  https://artifacts.picoctf.net/c/25/fixme1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.16, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 837 [application/octet-stream]
Saving to: 'fixme1.py'

fixme1.py               100%[=============================>]     837  --.-KB/s    in 0s      

2026-02-16 18:30:09 (53.9 MB/s) - 'fixme1.py' saved [837/837]

BelovedCis-picoctf@webshell:~$ python3 fixme1.py
  File "/home/BelovedCis-picoctf/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
BelovedCis-picoctf@webshell:~$ cat fixme1.py

import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x5a) + chr(0x07) + chr(0x00) + chr(0x46) + chr(0x0b) + chr(0x1a) + chr(0x5a) + chr(0x1d) + chr(0x1d) + chr(0x2a) + chr(0x06) + chr(0x1c) + chr(0x5a) + chr(0x5c) + chr(0x55) + chr(0x40) + chr(0x3a) + chr(0x58) + chr(0x0a) + chr(0x5d) + chr(0x53) + chr(0x43) + chr(0x06) + chr(0x56) + chr(0x0d) + chr(0x14)

  
flag = str_xor(flag_enc, 'enkidu')
  print('That is correct! Here\'s your flag: ' + flag)

BelovedCis-picoctf@webshell:~$ nano fixme1.py
BelovedCis-picoctf@webshell:~$ python3 fixme1.py
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_6a476c8f}
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{1nd3nt1ty_cr1515_6a476c8f}

## Notas

- Python utiliza la indentación para definir la estructura del código.
- Un error de indentación ocurre cuando una línea tiene más o menos espacios de los necesarios.
- La indentación incorrecta provoca errores como:

`IndentationError: unexpected indent`

- La función utilizada en el script emplea el operador XOR, el cual es común en técnicas de cifrado.
- El operador XOR permite cifrar y descifrar datos mediante una clave.
- El comando nano permite editar archivos directamente desde la terminal.
- El comando python3 ejecuta scripts escritos en Python versión 3.

Importancia en ciberseguridad:

Este ejercicio es relevante porque permite comprender cómo:

- Analizar código fuente
- Identificar errores en scripts
- Corregir fallos de ejecución
- Entender técnicas básicas de cifrado
- Ejecutar herramientas automatizadas

## Referencias

picoCTF. Plataforma educativa de ciberseguridad.

Python Software Foundation. Documentación oficial del lenguaje Python. [https://www.python.org](https://www.python.org)

Stallings, W. (2017). Network Security Essentials: Applications and Standards. Pearson.

Shotts, W. E. (2019). The Linux Command Line. No Starch Press.
Documentación oficial de Python. Manejo de indentación y sintaxis.