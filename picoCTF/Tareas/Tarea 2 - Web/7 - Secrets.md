## Secrets
## Descripcion

We have several pages hidden. Can you find the one with the flag?The website is running [here](http://saturn.picoctf.net:61923/).
## Solucion


### solucion 1 secret/hidden/superhidden

El reto consistió en realizar un proceso de **enumeración de directorios** dentro de una aplicación web. Al inspeccionar el código fuente de la página principal se encontraron referencias a carpetas ocultas que no estaban enlazadas en la interfaz del sitio. Siguiendo estas rutas manualmente (`/secrets`, `/hidden`, `/superhidden`) y revisando el código fuente en cada una de ellas, se logró localizar finalmente la página que contenía la flag. Este ejercicio demuestra cómo el análisis del código fuente puede revelar rutas internas dentro de una aplicación web.

picoCTF{succ3ss_@h3n1c@10n_790d2615}

## Notas

### Técnicas utilizadas

- Web Enumeration
    
- Directory Discovery
    
- Inspección de código HTML
    
- Navegación manual por rutas del servidor
    

### Conceptos de seguridad

**Directory Enumeration**  
Proceso de descubrir archivos o carpetas ocultas dentro de una aplicación web.

**Information Disclosure**  
Ocurre cuando el código fuente expone rutas internas o información sensible.

**Security Through Obscurity**  
Ocultar rutas no es una medida de seguridad efectiva si siguen siendo accesibles por URL.
## Referencias

