## Mind your Ps and Qs
## Descripcion

In RSA, a small e value can be problematic, but what about N? Can you decrypt this?[values](https://challenge-files.picoctf.net/c_wily_courier/8f75844947ccdb93020eecaf5eea8be97753b2075202328032bb4854ca7c6863/values)
## Solucion
La seguridad del algoritmo RSA se basa en la dificultad matemática de factorizar números primos gigantes.

- **RSA Seguro:** En el mundo real, la clave pública (el módulo $N$) tiene un tamaño de **2048 bits** o **4096 bits**. Romper esto tomaría millones de años con las computadoras actuales.
    
- **El Reto:** En este ejercicio, el valor de $N$ era de aproximadamente **253 bits**. Al ser tan pequeño, se vuelve trivial calcular los dos números primos originales ($p$ y $q$) que, multiplicados, dan como resultado $N$.

c = ...
n = ...
e = ...
 se obtienen de la factorizacion en factordb.com
p = ...
q = ...

tn = (p-1) * (q-1)
 
d = pow(e, -1, tn)
m = pow(c,d,n)

hex_str = hex(m)[2:]
 verifica que los digitos hexadecimales sean un numero par
if len(hex_str) % 2 != 0:
    hex_str = '0' + hex_str

decoded = bytes.fromhex(hex_str).decode()
print(f'\nDecodificado: {decoded}')

flag = decoded[::-1]
print(f'\nFlag : {flag}')

**picoCTF{sma11_N_n0_g0od_1dc7ae91}**
## Notas
Durante la resolución, aplicamos varios conceptos técnicos importantes de programación en Python:

- **Evitar el "Dependency Hell":** Inicialmente tuvimos problemas con la librería `pycryptodome`. Lo solucionamos utilizando funciones nativas.
    
- **Inverso Modular Nativo:** A partir de Python 3.8, la función `pow()` permite usar `-1` como exponente para calcular directamente el inverso modular: `pow(e, -1, phi)`. Esto elimina la necesidad de usar `Crypto.Util.number.inverse`.
    
- **El problema del Endianness (Orden de los bytes):** El texto nos salió al revés (`}19ea...{FTCocip`) porque al convertir el número gigante de vuelta a bytes ASCII, Python interpretó el orden de izquierda a derecha (Big-Endian). Al cambiar el argumento a `byteorder='little'`, Python lee los bytes desde el menos significativo, enderezando la flag.


## Referencias
- **FactorDB:** La base de datos pública más grande para buscar números factorizados. Herramienta obligatoria para CTFs de criptografía. (factordb.com)
    
- **Wikipedia - Algoritmo RSA:** Para entender la teoría y la historia detrás del algoritmo asimétrico más usado del mundo. (Búscalo como "RSA cryptosystem").
    
- **Python Docs - Función pow():** Para entender cómo la librería estándar de Python maneja las matemáticas de alta precisión sin librerías externas. (docs.python.org/3/library/functions.html#pow)
    
- **Endianness (Big-endian vs Little-endian):** Fundamental para retos de ingeniería inversa y criptografía. (Búscalo como "Endianness computer science").
- 