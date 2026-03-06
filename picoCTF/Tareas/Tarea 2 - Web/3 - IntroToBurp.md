## IntroToBurp
## Descripcion

Try [here](http://titan.picoctf.net:62445/) to find the flag
## Solucion


### solucion 1 usando burp

El reto consistió en analizar el funcionamiento de una aplicación web que implementaba un sistema de verificación mediante **OTP (One-Time Password)**. Para resolverlo se utilizó **Burp Suite**, una herramienta de análisis de tráfico HTTP que permite interceptar y modificar solicitudes enviadas entre el navegador y el servidor.

Primero se accedió al sitio web proporcionado por el reto de **picoCTF** y se completó el formulario inicial. Posteriormente, cuando el sistema solicitó un código OTP, se interceptó la solicitud HTTP utilizando Burp Suite. Al modificar la solicitud enviada al servidor (alterando o eliminando el parámetro del OTP), el sistema permitió el acceso sin validar correctamente el código.

Debido a esta mala validación del lado del servidor, se logró evadir el mecanismo de autenticación y obtener la flag:

**picoCTF{#0TP_Bypvss_SuCc3$S_c94b61ac}**
## Notas

### Herramienta utilizada

- **Burp Suite**  
    Permite interceptar, analizar y modificar solicitudes HTTP/HTTPS entre el cliente y el servidor.
### Procedimiento técnico

1. Acceder al sitio web del reto.
    
2. Configurar el navegador para que el tráfico pase por el proxy de Burp Suite.
    
3. Activar la opción **Intercept** en la pestaña Proxy.
    
4. Completar el formulario de registro en la página.
    
5. Interceptar la solicitud HTTP enviada durante la verificación OTP.
    
6. Modificar la solicitud HTTP (Parameter Tampering).
    
7. Enviar la solicitud alterada al servidor.
    
8. El servidor respondió con la flag al no validar correctamente el OTP.
### Conceptos de seguridad involucrados

**1. Intercepción de tráfico web**  
Las herramientas de proxy permiten observar y modificar solicitudes HTTP antes de que lleguen al servidor.

**2. Parameter Tampering**  
Es una vulnerabilidad donde un atacante manipula parámetros enviados en una solicitud HTTP para alterar el comportamiento del servidor.

**3. Validación del lado del servidor**  
Los sistemas seguros deben validar los datos recibidos en el backend. Si esta validación es incorrecta o inexistente, se pueden evadir mecanismos de seguridad.

**4. Bypass de autenticación**  
Cuando se logra acceder a una funcionalidad protegida sin cumplir los requisitos de autenticación.
### Aprendizaje del reto

El desafío demuestra la importancia de:

- Validar correctamente las solicitudes en el servidor.
    
- No confiar únicamente en controles implementados en el cliente.
    
- Implementar verificaciones robustas en sistemas de autenticación como OTP.

## Referencias

- PortSwigger  
    _Burp Suite Documentation_  
    [https://portswigger.net/burp](https://portswigger.net/burp)
- OWASP  
    _OWASP Web Security Testing Guide_  
    [https://owasp.org](https://owasp.org)
- The Web Application Hacker's Handbook  
    Stuttard, D., & Pinto, M. (2011). _The Web Application Hacker's Handbook: Finding and Exploiting Security Flaws._
    