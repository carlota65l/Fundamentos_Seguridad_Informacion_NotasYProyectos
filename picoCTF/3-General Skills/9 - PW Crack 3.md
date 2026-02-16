## PW Crack 3


## Descripcion

Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/18/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/18/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/18/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

## Solucion

### solucion 1_ usando python

se proporcionó un script en Python llamado `level3.py`, junto con dos archivos adicionales: `level3.flag.txt.enc`, que contiene la bandera cifrada, y `level3.hash.bin`, que contiene el hash de la contraseña correcta.

El objetivo de la actividad fue analizar el script para identificar la contraseña correcta entre siete posibles opciones incluidas en el código. El programa solicita al usuario una contraseña, genera su hash utilizando el algoritmo MD5 y lo compara con el hash almacenado en el archivo. Si los hashes coinciden, el programa descifra la bandera utilizando una operación XOR y la muestra en pantalla.

Para resolver el ejercicio, fue necesario analizar el código fuente, comprender el funcionamiento del algoritmo hash MD5 y probar las contraseñas posibles hasta encontrar la correcta.
 
```bash

```

Respuesta: picoCTF{m45h_fl1ng1ng_6f98a49f}

## Notas

El script utiliza la biblioteca hashlib de Python Software Foundation para generar un hash MD5 de la contraseña ingresada por el usuario:

`m = hashlib.md5() m.update(pw_bytes) return m.digest()`

El hash generado se compara con el hash almacenado en el archivo:

`correct_pw_hash = open('level3.hash.bin', 'rb').read()`

La comparación se realiza mediante:

`if( user_pw_hash == correct_pw_hash ):`

El algoritmo MD5 convierte una cadena de texto en un valor hash único de 128 bits. Este proceso es unidireccional, lo que significa que no se puede obtener directamente la contraseña original a partir del hash. Sin embargo, en este ejercicio se proporcionan siete posibles contraseñas, lo que permite probar cada una hasta encontrar la que genera el mismo hash.

Una vez encontrada la contraseña correcta, el script utiliza la función:

`str_xor(flag_enc.decode(), user_pw)`

para descifrar la bandera mediante la operación XOR, que es una técnica común de cifrado simétrico.

Este ejercicio demuestra el uso de funciones hash en sistemas de autenticación y la importancia de proteger las contraseñas mediante hash en lugar de almacenarlas como texto plano.
## Referencias

picoCTF  
[https://picoctf.org](https://picoctf.org)

Python Software Foundation  
[https://docs.python.org/3/library/hashlib.html](https://docs.python.org/3/library/hashlib.html)

Documentación oficial de hashlib  
[https://docs.python.org/3/library/hashlib.html](https://docs.python.org/3/library/hashlib.html)

Explicación del algoritmo MD5  
[https://en.wikipedia.org/wiki/MD5](https://en.wikipedia.org/wiki/MD5)

GCHQ — CyberChef (herramienta de análisis criptográfico)  
[https://gchq.github.io/CyberChef/](https://gchq.github.io/CyberChef/)