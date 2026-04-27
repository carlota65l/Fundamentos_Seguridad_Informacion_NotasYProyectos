## Crack the Power
## Descripcion
We received an encrypted message. The modulus is built from primes large enough that factoring them isn’t an option, at least not today. See if you can make sense of the numbers and reveal the flag.Download the [message](https://challenge-files.picoctf.net/c_amiable_citadel/4f048da6d1e55c5459752585d7c58f12d94f2b02fbe0fe739ad81716dc9191d0/message.txt).
## Solucion


````
import sympy
from Crypto.Util.number import long_to_bytes

# 1. Copia y pega aquí los valores que vienen en tu archivo message.txt
n = REEMPLAZA_ESTO_POR_EL_NUMERO_N
e = REEMPLAZA_ESTO_POR_EL_NUMERO_E  # Seguramente será 3
c = REEMPLAZA_ESTO_POR_EL_NUMERO_C

# 2. Como m^e < N, simplemente sacamos la raíz e-ésima de c
# sympy.integer_nthroot devuelve una tupla: (raíz, booleano_si_es_exacta)
m, is_exact = sympy.integer_nthroot(c, e)

if is_exact:
    print("¡Raíz exacta encontrada!")
    # 3. Convertir el número desencriptado a texto (bytes a ASCII)
    flag = long_to_bytes(m)
    print("Flag:", flag.decode('utf-8'))
else:
    print("La raíz no es exacta. Puede que haya un ligero padding de módulo (m^e > N por poco).")
````
### ¿Qué pasó matemáticamente?

Este es un caso clásico de un ataque de exponente público pequeño en RSA. Si analizamos las variables que te proporcionaron en el archivo `message.txt`, tenemos lo siguiente:

- **Módulo (n):** Un número gigantesco de cientos de dígitos.
    
- **Exponente (e):** 20 (un valor inusualmente pequeño, ya que el estándar suele ser 65537).
    
- **Texto Cifrado (c):** El mensaje encriptado.
    

Dado que la _flag_ es una cadena de texto muy corta, cuando se convirtió a número ($m$) y se elevó a la potencia de 20 para encriptarlo, el resultado fue **menor** que el módulo. Al cumplirse la condición de que $m^{20} < n$, no ocurrió ninguna reducción modular o "desbordamiento".

picoCTF{t1ny_e_837d7226}

## Notas

**Coppersmith's attack** describes a class of [cryptographic attacks](https://en.wikipedia.org/wiki/Cryptographic_attack "Cryptographic attack") on the [public-key cryptosystem](https://en.wikipedia.org/wiki/Public-key_cryptography "Public-key cryptography") [RSA](https://en.wikipedia.org/wiki/RSA_\(algorithm\) "RSA (algorithm)") based on the [Coppersmith method](https://en.wikipedia.org/wiki/Coppersmith_method "Coppersmith method"). Particular applications of the Coppersmith method for attacking RSA include cases when the public exponent _e_ is small or when partial knowledge of a prime factor of the secret key is available.
## Referencias
https://en.wikipedia.org/wiki/Coppersmith's_attack