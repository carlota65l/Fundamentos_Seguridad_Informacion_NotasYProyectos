## Local Authority
## Descripcion

Can you get the flag?Go to this [website](http://saturn.picoctf.net:50712/) and see what you can discover.
## Solucion

### solucion 1_jss

El reto consistió en analizar una aplicación web con un sistema de autenticación vulnerable. Al inspeccionar los archivos cargados por la página mediante las herramientas de desarrollador del navegador, se identificó un archivo JavaScript que contenía la función encargada de validar las credenciales de acceso. Dentro de este archivo se encontraron directamente el nombre de usuario y la contraseña utilizados por el sistema. Al ingresar estas credenciales en el formulario de inicio de sesión se obtuvo acceso al sistema y se mostró la flag. Este reto demuestra la inseguridad de realizar validaciones críticas del lado del cliente.

````
function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}
````
## Notas

### Herramientas utilizadas

- Inspector del navegador
    
- Visualización del código fuente
    
- Análisis de archivos JavaScript

### Conceptos de seguridad involucrados

**1. Client-Side Authentication**

- Ocurre cuando la validación del login se realiza en JavaScript.
    
- Es inseguro porque el código puede ser inspeccionado.

**2. Information Disclosure**

- Información sensible (credenciales) se encuentra expuesta en el código fuente.

**3. Reverse Engineering de JavaScript**

- Analizar archivos JS para entender la lógica de una aplicación web.
### Lección de seguridad

Las validaciones críticas como autenticación deben realizarse **en el servidor**, no en el cliente.
## Referencias

- PortSwigger  
    _Web Security Academy – Client-Side Vulnerabilities_  
    [https://portswigger.net/web-security](https://portswigger.net/web-security)
    
- Mozilla  
    _Using Browser Developer Tools_  
    [https://developer.mozilla.org](https://developer.mozilla.org)