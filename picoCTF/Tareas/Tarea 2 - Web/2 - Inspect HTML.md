## Inspect HTML
## Descripcion

Can you get the flag?Go to this [website](http://saturn.picoctf.net:56761/) and see what you can discover.
## Solucion


El desafío consistió en analizar una página web para descubrir información oculta utilizando herramientas del navegador. El reto hace referencia a **ocultar mensajes de manera indirecta**, inspirado en la historia de **Histiaeus**, relatada por **Herodotus**, donde un mensaje secreto se escondía bajo el cabello de un esclavo tatuado.

En el contexto del reto, el mensaje oculto se encontraba dentro del **código fuente HTML** de la página web.

---

### Procedimiento realizado

1. Se accedió al sitio web proporcionado por el reto de **picoCTF**.
    
2. Se abrió el **inspector del navegador** utilizando la herramienta de desarrollador (F12).
    
3. Se examinó la estructura HTML dentro de la pestaña **Elements** o **Inspector**.
    
4. Durante la revisión del código fuente se identificó un comentario o texto oculto que contenía la flag.
    
5. La flag encontrada fue:
    

**picoCTF{1n5p3t0r_0f_h7ml_1fd8425b}**
## Notas

**1. Inspección del código fuente**  
Las aplicaciones web envían al navegador el código HTML completo necesario para renderizar la página. Esto significa que cualquier usuario puede visualizar este código.

**2. Herramientas de desarrollador del navegador**  
Los navegadores modernos incluyen herramientas que permiten inspeccionar:

- HTML
    
- CSS
    
- JavaScript
    
- solicitudes de red
    
- almacenamiento local
    

Estas herramientas son fundamentales para la depuración y también para el análisis de seguridad.

**3. Exposición de información en el cliente**  
Ocultar datos sensibles en comentarios o elementos ocultos dentro del HTML no es seguro, ya que cualquier usuario puede acceder a ellos mediante el inspector.

### Aprendizaje del reto

Este desafío demuestra que:

- El **frontend nunca debe contener información sensible**.
    
- Los comentarios o datos ocultos en HTML pueden ser descubiertos fácilmente.
    
- Las herramientas de desarrollador son una parte esencial del análisis de aplicaciones web.
## Referencias
- Mozilla.  
    _Browser Developer Tools Documentation._  
    https://developer.mozilla.org/en-US/docs/Tools
- OWASP.  
    _OWASP Web Security Testing Guide._  
    [https://owasp.org](https://owasp.org)
- Wikipedia.  
    _Include Directive and Web Development Concepts._  
    [https://en.wikipedia.org](https://en.wikipedia.org)
- The Web Application Hacker's Handbook.  
    Stuttard, D., & Pinto, M. (2011). _The Web Application Hacker's Handbook: Finding and Exploiting Security Flaws._