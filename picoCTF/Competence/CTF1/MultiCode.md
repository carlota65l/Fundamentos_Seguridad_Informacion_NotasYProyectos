## MultiCode
## Descripcion
We intercepted a suspiciously encoded message, but it’s clearly hiding a flag. No encryption, just multiple layers of obfuscation. Can you peel back the layers and reveal the truth?Download the [message](https://challenge-files.picoctf.net/c_plain_mesa/b3a8655f3bca197c0226d40b8482562895c5cb27913567e76f87f0c78743ede2/message.txt).
## Solucion
El mensaje proporcionado fue:

NjM3NjcwNjI1MDQ3NTMyNTM3NDI2MTcyNjY2NzcyNzE1ZjcyNjE3MDMwNzE3NjYxNzQ1ZjM0MzgzMTczMzAzNjM0NzAyNTM3NDQ=

Se aplicaron las siguientes decodificaciones:

1. **Base64 decode**
    

Resultado:

637670625047532537426172666772715f72617030717661745f3438317330363470253744

2. **Hex decode**
    

Resultado:

cvpbPGS%7Barfggrq_rap0qvat_481s064p%7D

3. **URL decode**
    

Resultado:

cvpbPGS{arfggrq_rap0qvat_481s064p}

4. **ROT13**

Resultado final:

**picoCTF{nested_enc0ding_481f064c}**

## Notas
## Base64

Base64 es un esquema de codificación que convierte datos binarios en texto ASCII utilizando un conjunto de 64 caracteres.

Características:

- Usa letras, números y símbolos `+` y `/`
    
- Suele terminar con `=` o `==` como padding
    
- Es común en correos electrónicos, APIs y transferencia de datos
    

Ejemplo:

cGljb0NURg==

Decodificación:

picoCTF
## Referencias
Durante la resolución del reto se pueden utilizar herramientas como:
- Terminal de Linux
- Python
- OpenSSL
- CyberChef

Una herramienta muy útil para este tipo de retos es **CyberChef**, ya que permite aplicar múltiples operaciones de codificación y decodificación de forma visual.

1. **picoCTF**. (2024). _picoCTF Platform_.  
    [https://picoctf.org/](https://picoctf.org/)
    
2. **CyberChef**. (2024). _The Cyber Swiss Army Knife_.  
    [https://gchq.github.io/CyberChef/](https://gchq.github.io/CyberChef/)
    
3. **RFC 4648**.  
    The Base16, Base32, and Base64 Data Encodings.
    
4. Fielding, R. (2014). _Hypertext Transfer Protocol (HTTP/1.1)_.  
    IETF RFC 7230.