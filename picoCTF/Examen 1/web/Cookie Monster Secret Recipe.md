## ### Cookie Monster Secret Recipe

## Descripcion

## Solucion
- Acceder al sitio del reto.
- Abrir herramientas de desarrollador (**F12**).
- Revisar las **cookies del navegador**.
- Encontrar el cookie `secret_recipe`.
- Decodificar su valor:
    - URL Decode
    - Base64 Decode
- Obtener la flag.

**picoCTF{c00k1e_m0nster_l0ves_c00kies_73110ED1}**

## Notas
#### Cookies en aplicaciones web

Las cookies son utilizadas por los sitios web para almacenar información como:

- sesiones de usuario
    
- preferencias
    
- tokens de autenticación
    

Sin embargo, almacenar información sensible en cookies sin protección puede representar un **riesgo de seguridad**.

#### Codificación Base64

Base64 es un método de codificación que convierte datos binarios en texto utilizando caracteres ASCII. No es un método de cifrado, ya que puede revertirse fácilmente mediante decodificación.

#### Uso de herramientas del navegador

Las herramientas de desarrollo permiten inspeccionar:
- cookies
- almacenamiento local
- código fuente
- solicitudes HTTP

Estas herramientas son fundamentales para el **análisis de seguridad web**.

## Referencias
https://gchq.github.io/CyberChef/
Mozilla Foundation – Documentación sobre cookies HTTP.  
[https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)