##  PW Crack 2
## Descripcion

Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/15/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/15/level2.flag.txt.enc) in the same directory too.
## Solucion
### solucion 1_ usando python


se proporcionó un script en Python llamado `level2.py` junto con un archivo cifrado llamado `level2.flag.txt.enc`. El objetivo fue analizar el código fuente del script para descubrir la contraseña correcta y utilizarla para descifrar la bandera (flag).

El programa solicita al usuario una contraseña y la compara con una cadena generada mediante la función `chr()`, que convierte valores numéricos en caracteres ASCII. Una vez introducida la contraseña correcta, el programa utiliza una función de cifrado XOR para descifrar el contenido del archivo cifrado y mostrar la bandera en pantalla.
 
```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/15/level2.py
--2026-02-16 19:02:37--  https://artifacts.picoctf.net/c/15/level2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.92, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 914 [application/octet-stream]
Saving to: 'level2.py'

level2.py               100%[=============================>]     914  --.-KB/s    in 0s      

2026-02-16 19:02:37 (327 MB/s) - 'level2.py' saved [914/914]

BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/15/level2.flag.txt.enc
--2026-02-16 19:02:37--  https://artifacts.picoctf.net/c/15/level2.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.92, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level2.flag.txt.enc'

level2.flag.txt.enc     100%[=============================>]      31  --.-KB/s    in 0s      

2026-02-16 19:02:37 (8.80 MB/s) - 'level2.flag.txt.enc' saved [31/31]

BelovedCis-picoctf@webshell:~$ ls
README.txt  fixme2.py  level1.flag.txt.enc  level1.py  level2.flag.txt.enc  level2.py
BelovedCis-picoctf@webshell:~$ cat level2.py
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

flag_enc = open('level2.flag.txt.enc', 'rb').read()



def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_2_pw_check()
BelovedCis-picoctf@webshell:~$ python3 level2.py
Please enter correct password for flag: 39ce
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_502ec42e}
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{tr45h_51ng1ng_502ec42e}


El script contiene la siguiente condición:

`if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):`

La función `chr()` convierte un número en su carácter ASCII correspondiente.

Conversión:

|Valor Hexadecimal|ASCII|
|---|---|
|0x33|3|
|0x39|9|
|0x63|c|
|0x65|e|

Resultado:

`39ce`

Cuando se introduce esta contraseña, el programa ejecuta la función:

`decryption = str_xor(flag_enc.decode(), user_pw)`

Esta función aplica la operación XOR entre el texto cifrado y la contraseña, lo que permite recuperar el texto original (la bandera).

## Notas


## Referencias
picoCTF  
[https://picoctf.org](https://picoctf.org)


Tabla ASCII  
[https://www.asciitable.com](https://www.asciitable.com)

Concepto de cifrado XOR  
[https://en.wikipedia.org/wiki/XOR_cipher](https://en.wikipedia.org/wiki/XOR_cipher)