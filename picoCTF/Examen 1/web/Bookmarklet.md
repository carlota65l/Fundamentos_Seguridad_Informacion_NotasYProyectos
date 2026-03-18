## Bookmarklet

## Descripcion
Why search for the flag when I can make a bookmarklet to print it for me? http://titan.picoctf.net:62265/
## Solucion

1. Acceder a la página del reto.
    
2. Inspeccionar el código del bookmarklet.
    
3. Copiar el código JavaScript.
    
4. Abrir las herramientas de desarrollo del navegador (F12).
    
5. Ejecutar el código en la consola eliminando el prefijo `javascript:`.
    
6. El script descifra el mensaje y muestra la **flag**.

El script descifra la cadena cifrada y revela la siguiente flag:
**picoCTF{p@g3_turn3r_6bbf8953}**
## Notas
#### Bookmarklets

Un bookmarklet es un fragmento de JavaScript almacenado como un marcador del navegador que puede ejecutarse en cualquier página web. Estos pueden utilizarse para automatizar tareas o manipular contenido de páginas.

#### Seguridad del lado del cliente

Este reto demuestra que **la información sensible no debe almacenarse en código del lado del cliente**, ya que cualquier usuario puede inspeccionar o ejecutar el código JavaScript desde las herramientas de desarrollo del navegador.

#### Ofuscación básica

El reto utiliza una técnica simple de ofuscación mediante operaciones sobre códigos ASCII. Sin embargo, este tipo de protección es fácilmente reversible si el algoritmo está disponible.

## Referencias
- picoCTF. _picoCTF Practice Challenges_.  
    [https://picoctf.org](https://picoctf.org)
- Mozilla Foundation. _JavaScript Guide_.  
    [https://developer.mozilla.org/en-US/docs/Web/JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- Mozilla Foundation. _Bookmarklets_.  
    https://developer.mozilla.org/en-US/docs/Web/JavaScript/Bookmarklets
- OWASP. _Client-Side Security Risks_.  
    [https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/)
- OWASP. _JavaScript Security_.  
    [https://owasp.org/www-community/attacks/](https://owasp.org/www-community/attacks/)