##   PW Crack 1
## Descripcion

Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/12/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/12/level1.flag.txt.enc) in the same directory too.
## Solucion
### solucion 1_ usando python

analizar un script en Python llamado `level1.py`, el cual forma parte de un reto de criptografía de la plataforma picoCTF, desarrollada por Carnegie Mellon University. El objetivo principal es identificar la contraseña correcta que permite descifrar un archivo cifrado que contiene una bandera (flag), la cual representa la solución del reto.

El script proporcionado solicita al usuario ingresar una contraseña y, si esta es correcta, utiliza una función de cifrado basada en la operación XOR para descifrar el contenido del archivo `level1.flag.txt.enc`. Este archivo contiene la flag cifrada, y solo puede ser descifrada mediante el uso de la contraseña correcta.

```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/12/level1.py
--2026-02-16 18:43:29--  https://artifacts.picoctf.net/c/12/level1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 876 [application/octet-stream]
Saving to: 'level1.py'

level1.py               100%[=============================>]     876  --.-KB/s    in 0s      

2026-02-16 18:43:30 (33.1 MB/s) - 'level1.py' saved [876/876]

BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/12/level1.flag.txt.enc
--2026-02-16 18:43:34--  https://artifacts.picoctf.net/c/12/level1.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.16, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30 [application/octet-stream]
Saving to: 'level1.flag.txt.enc'

level1.flag.txt.enc     100%[=============================>]      30  --.-KB/s    in 0s      

2026-02-16 18:43:34 (11.8 MB/s) - 'level1.flag.txt.enc' saved [30/30]

BelovedCis-picoctf@webshell:~$ ls
README.txt  fixme2.py  level1.flag.txt.enc  level1.py
BelovedCis-picoctf@webshell:~$ cat level1.py
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################


flag_enc = open('level1.flag.txt.enc', 'rb').read()



def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "8713"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_1_pw_check()
BelovedCis-picoctf@webshell:~$ python3 level1.py
Please enter correct password for flag: 8713
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_1b2fd683}
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{}


1. Descarga de los archivos proporcionados mediante el comando `wget`.
2. Verificación de los archivos descargados usando el comando `ls`.
3. Visualización del contenido del script mediante el comando:

`cat level1.py`

4. Análisis del código fuente para identificar la contraseña correcta.
5. Identificación de la contraseña dentro de la condición:

`if( user_pw == "8713"):`

6. Ejecución del script usando:

`python3 level1.py`

7. Introducción de la contraseña correcta para obtener la flag.
8. Descifrado exitoso del archivo cifrado mediante la función XOR.

## Notas

La contraseña no estaba protegida, ya que se encontraba visible en el código fuente.

• Este tipo de vulnerabilidad se conoce como **hardcoded password**, lo cual representa una mala práctica de seguridad.

• El cifrado XOR es fácil de implementar pero también fácil de romper si la clave es conocida.

• El análisis estático del código fue suficiente para resolver el ejercicio.

• No fue necesario realizar ataques de fuerza bruta ni utilizar herramientas externas.

• Este ejercicio demuestra la importancia del análisis de código en la ciberseguridad.
## Referencias

picoCTF. (2026). Cryptography Challenge Level 1.  
Carnegie Mellon University. (2026). picoCTF Cybersecurity Training Platform.
Python Software Foundation. (2024). Python Documentation.  
[https://docs.python.org](https://docs.python.org)
Stallings, W. (2017). Cryptography and Network Security: Principles and Practice. Pearson.
Singh, S. (2000). The Code Book: The Science of Secrecy from Ancient Egypt to Quantum Cryptography. Anchor Books.