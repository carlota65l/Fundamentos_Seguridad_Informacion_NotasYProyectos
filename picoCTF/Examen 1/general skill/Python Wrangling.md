## Python Wrangling

## Descripcion
Python scripts are invoked kind of like programs in the Terminal...Can you run [ende.py](https://challenge-files.picoctf.net/c_wily_courier/0d4c2d3266a170a6b1cc9150c9a1cf489cd39be1968f82164aea44fb88e810b7/ende.py) using [password.txt](https://challenge-files.picoctf.net/c_wily_courier/0d4c2d3266a170a6b1cc9150c9a1cf489cd39be1968f82164aea44fb88e810b7/password.txt) to get [flag.txt.en](https://challenge-files.picoctf.net/c_wily_courier/0d4c2d3266a170a6b1cc9150c9a1cf489cd39be1968f82164aea44fb88e810b7/flag.txt.en)?
## Solucion
### Ejecución de scripts en Python

- Los scripts se ejecutan como programas desde la terminal:
    
    python3 script.py
    
- Este reto enseña el uso de **argumentos en línea de comandos (`sys.argv`)**.
#### Parámetros del script

El script muestra:

Usage: ende.py (-e/-d) [file]

- `-e` → encrypt (cifrar)
- `-d` → decrypt (descifrar)
#### Uso de la contraseña

- El programa solicita una contraseña o la recibe como argumento
- La contraseña proviene del archivo `pw.txt`
- Se puede automatizar con:
    
    python3 ende.py -d flag.txt.en $(cat pw.txt)


**picoCTF{4p0110_1n_7h3_h0us3_9c5f9bcf}**
## Notas

### Criptografía usada

El script utiliza:

- `base64` → para codificar la contraseña
- `Fernet` (librería `cryptography`) → para cifrado simétrico

Flujo:

1. Contraseña → convertida a base64
2. Se crea clave Fernet
3. Se descifra `flag.txt.en`
4. Se imprime la flag
## Referencias
- [Writeup en CTFtime](https://ctftime.org/writeup/28917?utm_source=chatgpt.com)
- [Writeup técnico (DMFR Security)](https://dmfrsecurity.com/2021/04/19/picoctf-2021-python-wrangling-writeup/?utm_source=chatgpt.com)
- [Guía paso a paso (Jun Wei Tan)](https://tan-junwei.github.io/CTF-Writeups/PicoCTF/General-Skills/Python-Wrangling?utm_source=chatgpt.com)
- [Otra solución documentada](https://ctftime.org/writeup/28149?utm_source=chatgpt.com)
- [Explicación completa del reto](https://ahmedheltaher.github.io/ctf-writeups/sites/picoCTF/General-Skills/Python-Wrangling.html?utm_source=chatgpt.com)