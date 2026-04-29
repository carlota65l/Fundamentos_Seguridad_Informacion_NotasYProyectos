## vault-door-5
## Descripcion
In the last challenge, you mastered octal (base 8), decimal (base 10), and hexadecimal (base 16) numbers, but this vault door uses a different change of base as well as URL encoding!The source code for this vault is here: [VaultDoor5.java](https://challenge-files.picoctf.net/c_fickle_tempest/aee691634d8cfd4a10820634bdea6b80aa104301e4b83d01fd4d176098d69e99/VaultDoor5.java)
## Solucion

- Examinamos el código fuente en Java que se nos da
- La flag esta codificada con :  URL Encode y Base64 hay que revertilos
### Forma 1 - javascript
- Ejecutamos el siguiente código en una consola de javascript en el navegador
```javascript
cad = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVmJTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2JTM0JTVmJTMwJTYyJTM5JTM1JTM3JTYzJTM0JTY2"

cad2 = atob(cad)

flag = decodeURIComponent(cad2)
```
## Forma 2 - Python
- Ejecutamos el siguiente script en el iterprete de python
```python
>>> from base64 import b64decode
>>> from urllib.parse import unquote
>>> cad = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVmJTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2JTM0JTVmJTMwJTYyJTM5JTM1JTM3JTYzJTM0JTY2"
>>> cad2 = b64decode(cad)
>>> cad2
b'%63%30%6e%76%33%72%74%31%6e%67%5f%66%72%30%6d%5f%62%61%35%65%5f%36%34%5f%30%62%39%35%37%63%34%66'
>>> flag = unquote(cad2)
>>> flag
```
### Forma3 - cyberchef
- Ir a Cyberchef: https://gchq.github.io/CyberChef/
- Usar la recetas: From Base64 y URL Decode

**picoCTF{c0nv3rt1ng_fr0m_ba5e_64_ed0b4288}**
## Notas
#### ¿Cómo funciona esta puerta?

Si revisamos la función `checkPassword`, el programa realiza dos pasos sobre la contraseña antes de compararla:

1. **URL Encoding:** Codifica tu entrada (`urlEncode`).
    
2. **Base64 Encoding:** Codifica el resultado del paso anterior en Base64 (`base64Encode`).
    

Después, compara el resultado con esta cadena larga: `JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVmJTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2JTM0JTVmJTY1JTY0JTMwJTYyJTM0JTMyJTM4JTM4`

##### Deshaciendo la seguridad (Ingeniería Inversa)

Para recuperar la contraseña original, solo tenemos que tomar esa cadena gigante y aplicar los procesos a la inversa:

**Paso 1: Decodificar el Base64** Si tomamos la cadena `JTYzJTM...` y la pasamos por un decodificador de Base64 (puedes usar herramientas como CyberChef o la terminal), obtenemos este texto:

> `%63%30%6e%76%33%72%74%31%6e%67%5f%66%72%30%6d%5f%62%61%35%65%5f%36%34%5f%65%64%30%62%34%32%38%38`

**Paso 2: Decodificar el URL Encoding** Como dijo el Minion #2415, esto parece código de una página web. El formato `%xx` representa caracteres en sistema hexadecimal. Si decodificamos esta URL (traduciendo los valores hexadecimales a texto ASCII), obtenemos nuestra contraseña en claro. Por ejemplo, `%63` es la letra `c`, `%30` es `0`, y así sucesivamente.

Al decodificarlo todo, obtenemos: `c0nv3rt1ng_fr0m_ba5e_64_ed0b4288` _(convirtiendo desde base 64)._
## Referencias
 - Cyberchef: https://gchq.github.io/CyberChef/