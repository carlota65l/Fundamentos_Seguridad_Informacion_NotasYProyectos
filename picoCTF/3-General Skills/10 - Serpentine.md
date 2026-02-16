## Serpentine
## Descripcion

Find the flag in the Python script![Download Python script](https://artifacts.picoctf.net/c/35/serpentine.py)
## Solucion
### solucion 1_ usando python


un script en Python llamado `serpentine.py`. El programa simula una interfaz interactiva que permite al usuario elegir entre mostrar mensajes de motivación, mostrar la bandera o salir del programa.

Sin embargo, al seleccionar la opción para mostrar la bandera, el programa indica que la función ha sido extraviada. El objetivo del ejercicio fue analizar el código fuente para localizar la función responsable de descifrar la bandera y ejecutarla manualmente.

Mediante la revisión del script, se identificó que la bandera estaba almacenada en una variable cifrada y que existía una función que permitía descifrarla utilizando una operación XOR con una clave específica. Aunque la función no era llamada por el programa principal, fue posible ejecutarla directamente desde el entorno de Python para obtener la bandera.

 
```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/35/serpentine.py
--2026-02-16 21:34:34--  https://artifacts.picoctf.net/c/35/serpentine.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.16, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2550 (2.5K) [application/octet-stream]
Saving to: 'serpentine.py'

serpentine.py           100%[============================>]   2.49K  --.-KB/s    in 0s      

2026-02-16 21:34:34 (962 MB/s) - 'serpentine.py' saved [2550/2550]

BelovedCis-picoctf@webshell:~$ ls
README.txt  serpentine.py
BelovedCis-picoctf@webshell:~$ cat serpentine.py

import random
import sys



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x5c) + chr(0x01) + chr(0x57) + chr(0x2a) + chr(0x17) + chr(0x5e) + chr(0x5f) + chr(0x0d) + chr(0x3b) + chr(0x19) + chr(0x56) + chr(0x5b) + chr(0x5e) + chr(0x36) + chr(0x53) + chr(0x07) + chr(0x51) + chr(0x18) + chr(0x58) + chr(0x05) + chr(0x57) + chr(0x11) + chr(0x3a) + chr(0x0f) + chr(0x0e) + chr(0x59) + chr(0x06) + chr(0x4d) + chr(0x55) + chr(0x0c) + chr(0x0f) + chr(0x14)


def print_flag():
  flag = str_xor(flag_enc, 'enkidu')
  print(flag)


def print_encouragement():
  encouragements = ['You can do it!', 'Keep it up!', 
                    'Look how far you\'ve come!']
  choice = random.choice(range(0, len(encouragements)))
  print('\n-----------------------------------------------------')
  print(encouragements[choice])
  print('-----------------------------------------------------\n\n')



def main():

  print(
'''
    Y
  .-^-.
 /     \      .- ~ ~ -.
()     ()    /   _ _   `.                     _ _ _
 \_   _/    /  /     \   \                . ~  _ _  ~ .
   | |     /  /       \   \             .' .~       ~-. `.
   | |    /  /         )   )           /  /             `.`.
   \ \_ _/  /         /   /           /  /                `'
    \_ _ _.'         /   /           (  (
                    /   /             \  \\
                   /   /               \  \\
                  /   /                 )  )
                 (   (                 /  /
                  `.  `.             .'  /
                    `.   ~ - - - - ~   .'
                       ~ . _ _ _ _ . ~
'''
  )
  print('Welcome to the serpentine encourager!\n\n')
  
  while True:
    print('a) Print encouragement')
    print('b) Print flag')
    print('c) Quit\n')
    choice = input('What would you like to do? (a/b/c) ')
    
    if choice == 'a':
      print_encouragement()
      
    elif choice == 'b':
      print('\nOops! I must have misplaced the print_flag function! Check my source code!\n\n')
      
    elif choice == 'c':
      sys.exit(0)
      
    else:
      print('\nI did not understand "' + choice + '", input only "a", "b" or "c"\n\n')



if __name__ == "__main__":
  main()

BelovedCis-picoctf@webshell:~$ python3
Python 3.10.12 (main, Feb  4 2025, 14:57:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import serpentine
>>> serpentine.print_flag()
picoCTF{7h3_r04d_l355_7r4v3l3d_ae0b80bd}
>>> exit()
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{7h3_r04d_l355_7r4v3l3d_ae0b80bd}

## Notas

**Archivo utilizado:**

`serpentine.py`

**Comando para descargar el archivo:**

`wget https://artifacts.picoctf.net/c/35/serpentine.py`

**Comando para ver el contenido del archivo:**

`cat serpentine.py`

**Función encontrada que descifra la bandera:**

`def print_flag():   flag = str_xor(flag_enc, 'enkidu')   print(flag)`

**Comando utilizado para ejecutar la función manualmente:**

`python3 -c "import serpentine; serpentine.print_flag()"`

Conceptos aprendidos:

- Análisis de código fuente    
- Uso de Python en ciberseguridad
- Identificación de funciones ocultas
- Cifrado y descifrado con XOR
- Ejecución de funciones desde la terminal
## Referencias

picoCTF  
[https://picoctf.org](https://picoctf.org)

Python Software Foundation  
[https://www.python.org](https://www.python.org)

Explicación del cifrado XOR  
[https://en.wikipedia.org/wiki/XOR_cipher](https://en.wikipedia.org/wiki/XOR_cipher)

Conceptos básicos de ingeniería inversa  
https://owasp.org/www-community/controls/Reverse_Engineering