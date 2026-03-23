## findme

## Descripcion
Help us test the form by submiting the username as `test` and password as `test!`The website running [here](http://saturn.picoctf.net:55455/).
## Solucion
heat Sheet (Comandos útiles)
**Petición HTTP POST Cruda (Para Burp Suite):**

HTTP

```
POST /login HTTP/1.1
Host: saturn.picoctf.net:58052
Content-Type: application/x-www-form-urlencoded
Content-Length: 28

username=test&password=test!
```
**picoCTF{proxies_all_the_way_d1c0b112}**
## Notas
- **Códigos de Estado HTTP (302 Found):**
    
    - Cuando un inicio de sesión es exitoso, los servidores suelen responder con un código `302 Found` (o `301`, `307`).
        
    - Este código le dice al cliente: _"Todo bien, pero la página que buscas ahora está en esta otra dirección"_.
        
    - **El problema de los navegadores:** Chrome, Firefox, etc., siguen estas redirecciones de forma automática y en milisegundos. Si hay información secreta en esa respuesta intermedia (como una flag), el usuario normal nunca la verá.
        
- **La Cabecera `Location`:**
    
    - Es la cabecera HTTP que acompaña al código 302. Indica la URL exacta a la que debe saltar el cliente.
        
    - _Ejemplo:_ `Location: /next-page?id=cGljb0NURnt...`
        
- **Codificación Base64:**
    
    - Es un método para convertir datos binarios o texto especial en una cadena de texto ASCII segura para ser transmitida por URLs o HTTP.
        
    - **Cómo reconocerlo:** Suele contener letras mayúsculas, minúsculas, números y frecuentemente termina con uno o dos signos de igual (`=`) conocidos como _padding_.
        
    - **Importante:** Base64 es _codificación_, no _encriptación_. Cualquiera puede decodificarlo.
## Referencias
- **Mozilla Developer Network (MDN) - HTTP 302:** [https://developer.mozilla.org/es/docs/Web/HTTP/Status/302](https://developer.mozilla.org/es/docs/Web/HTTP/Status/302)
- **MDN - Redirecciones HTTP:** [https://developer.mozilla.org/es/docs/Web/HTTP/Redirections](https://www.google.com/search?q=https://developer.mozilla.org/es/docs/Web/HTTP/Redirections)
- **CyberChef (La navaja suiza para decodificar Base64 y más):** [https://gchq.github.io/CyberChef/](https://gchq.github.io/CyberChef/)
- **Explicación visual de Base64:** [https://es.wikipedia.org/wiki/Base64](https://es.wikipedia.org/wiki/Base64)