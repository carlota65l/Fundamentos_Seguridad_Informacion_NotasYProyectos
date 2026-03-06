## Includes
## Descripcion

Can you get the flag?Go to this [website](http://saturn.picoctf.net:50003/) and see what you can discover.
## Solucion


### solucion 1

El reto consistió en analizar una página web para encontrar una **flag oculta**. Para resolverlo se inspeccionó el código fuente de la página utilizando las herramientas de desarrollador del navegador. Durante la revisión se identificó que el archivo HTML principal incluía otros archivos externos, específicamente un archivo de estilos **CSS** y un archivo **JavaScript**.

Al revisar estos archivos incluidos, se encontraron comentarios dentro del código que contenían partes de la flag. Posteriormente, se unieron ambas partes encontradas en los archivos `style.css` y `script.js`, lo que permitió reconstruir la flag completa:
**picoCTF{1nclu51v17y_1of2_f7w_2of2_b8f4b022}**

## Notas

- Los navegadores descargan todos los recursos necesarios para mostrar una página web, incluyendo:
    
    - HTML
        
    - CSS
        
    - JavaScript
        
    - imágenes y otros recursos.
        
- Muchas páginas utilizan **archivos incluidos** para organizar el código y mejorar la reutilización.
    
- Los comentarios dentro del código pueden revelar información sensible si no se eliminan antes de publicar la aplicación.
    
- Las herramientas de desarrollador permiten analizar fácilmente los recursos cargados por una página.
    

### Pasos técnicos utilizados

1. Abrir la página del reto en el navegador.
    
2. Abrir las herramientas de desarrollador (F12).
    
3. Revisar el código fuente y los archivos cargados por la página.
    
4. Analizar los archivos incluidos:
    
    - `style.css`
        
    - `script.js`
        
5. Encontrar partes de la flag dentro de comentarios del código.
    
6. Combinar ambas partes para formar la flag completa.
    
 Conceptos de ciberseguridad relacionados

- **Information Disclosure**

- **Client-Side Security**    
- **Source Code Inspection**

- **Web Application Enumeration**


Este tipo de retos enseña que **ocultar información en el lado del cliente no es seguro**, ya que cualquier usuario puede inspeccionar los archivos descargados por el navegador.

## Referencias

- picoCTF. (2024). _picoCTF Challenges and Learning Platform_.  
    [https://picoctf.org](https://picoctf.org)
    
- Mozilla. (2024). _Firefox Developer Tools Documentation_.  
    https://developer.mozilla.org/en-US/docs/Tools
    
- OWASP. (2023). _Web Security Testing Guide_.  
    [https://owasp.org](https://owasp.org)
    
- Wikipedia. _Include directive in programming languages_.  
    [https://en.wikipedia.org/wiki/Include_directive](https://en.wikipedia.org/wiki/Include_directive)