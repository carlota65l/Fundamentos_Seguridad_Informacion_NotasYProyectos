##  GET aHEAD
## Descripcion
Find the flag being held on this server to get ahead of the competitionhttp://wily-courier.picoctf.net:57743/
## Solucion


El servidor está configurado para:

- Ocultar la bandera del contenido HTML
    
- Pero incluir la bandera dentro de los **headers**
    
- Solo mostrar ese header cuando se usa el método HEAD
    

En tu captura aparece:

flag: picoCTF{rBj3ct_tn3_du4l1ty_8b13f07}

Ese valor está en los encabezados de la respuesta.


### solucion 2_terminal

Con curl:

curl -I http://wily-courier.picoctf.net:57743/index.php

o

curl -X HEAD http://wily-courier.picoctf.net:57743/index.php

La opción `-I` usa HEAD automáticamente.

## Notas

#### Diferencia entre GET y HEAD

Ambos son métodos HTTP, pero tienen una diferencia clave:

- **GET**
    
    - Solicita el recurso completo.
        
    - El servidor responde con:
        
        - Encabezados (headers)
            
        - Cuerpo (body) → contenido HTML
            
- **HEAD**
    
    - Solicita únicamente los encabezados.
        
    - El servidor responde con:
        
        - Encabezados
            
        - ❌ Sin cuerpo
            

Ejemplo:

GET devuelve:

HTTP/1.1 200 OK  
Content-Type: text/html  
  
<html>contenido...</html>

HEAD devuelve:

HTTP/1.1 200 OK  
Content-Type: text/html  
flag: picoCTF{...}
## Referencias

- http methods - [https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods "https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods")
- web proxy - [https://learn.onemonth.com/web-hacking-tools-proxies/](https://learn.onemonth.com/web-hacking-tools-proxies/ "https://learn.onemonth.com/web-hacking-tools-proxies/")