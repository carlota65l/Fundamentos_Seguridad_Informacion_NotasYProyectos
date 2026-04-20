## b00tl3gRSA2
## Descripcion

In RSA d is a lot bigger than e, why don't we use d to encrypt instead of e?
Connect with nc fickle-tempest.picoctf.net 51992.
## Solucion
El reto presentó una implementación atípica del algoritmo RSA. En lugar de usar un exponente público convencional y pequeño (como 65537), el servidor utilizó un número gigantesco para cifrar. La pista principal del reto insinuaba que se estaban invirtiendo los roles de las claves: el exponente $d$ se usaba para cifrar en lugar de $e$.

c = ...
n = ...
e = ...

e = 65537
m = pow(c,e,n)
print(m)

flag = bytes.fromhex(hex(m)[2:]).decode()

print(flag)

**picoCTF{bad_1d3a5_3801255}**

## Notas

- **Recolección de datos:** Se capturaron el texto cifrado ($c$), el módulo ($n$) y el exponente público ($e$) proporcionados por el servidor a través de una conexión `netcat`.
    
- **Explotación:** Se utilizó el módulo de Python `owiener` para ejecutar el algoritmo matemático sobre $n$ y $e$, recuperando exitosamente el exponente privado $d$.
## Referencias
- **El Ataque de Wiener (Wikipedia):** Explicación teórica profunda sobre el teorema de las fracciones continuas aplicadas a RSA. [https://en.wikipedia.org/wiki/Wiener%27s_attack](https://en.wikipedia.org/wiki/Wiener%27s_attack)
    
- **Repositorio de la librería `owiener`:** Herramienta en Python utilizada para automatizar la extracción de la clave privada débil. [https://github.com/orisano/owiener](https://github.com/orisano/owiener)
    
- **PyCryptodome (`long_to_bytes`):** Documentación oficial de la librería estándar para operaciones criptográficas en Python, usada para convertir el bloque numérico en texto legible. [https://pycryptodome.readthedocs.io/](https://pycryptodome.readthedocs.io/)
    
- **Documentación de PEP 668:** Explicación oficial de Python sobre por qué ocurren los errores de "entorno administrado externamente" en sistemas Linux modernos. [https://peps.python.org/pep-0668/](https://peps.python.org/pep-0668/)