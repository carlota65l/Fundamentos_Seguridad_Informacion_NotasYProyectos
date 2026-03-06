## Power Cookie
## Descripcion


## Solucion


### solucion 1

Busca una cookie a:
isAdmin
Muchas veces su valor será: 0

#### Modificar la cookie

Cambia el valor de la cookie:
0 → 1
#### Recargar la página
Después de modificar la cookie:
Refresh (F5)

El servidor ahora creerá que eres **administrador** y mostrará la **flag**.


**picoCTF{gr4d3_A_c00k13_0d351e23}**
## Notas
**Herramientas utilizadas**
- Herramientas de desarrollador del navegador

- Edición manual de cookies

**Conceptos de seguridad**

- Cookie Manipulation
    
- Client-Side Trust
    
- Privilege Escalation
    
- Session Management

**Lección de seguridad**

Las cookies nunca deben almacenar **información sensible sin protección**, y el servidor siempre debe validar los privilegios del usuario.

## Referencias

- Mozilla  
    _HTTP Cookies Documentation_  
    [https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
    
- PortSwigger  
    _Web Security Academy – Cookie Vulnerabilities_  
    [https://portswigger.net/web-security](https://portswigger.net/web-security)