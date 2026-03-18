## head-dump

## Descripcion
Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag. The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden. The website is running picoCTF News. http://verbal-sleep.picoctf.net:49980/

El reto presenta una página de blog donde se publican artículos, incluyendo uno relacionado con **API Documentation**. El objetivo es explorar la aplicación web y encontrar un **endpoint oculto** que expone un archivo que contiene información de la memoria del servidor.
## Solucion
#### Exploración del sitio

Primero se navega por el sitio:

http://verbal-sleep.picoctf.net:49980/

Se revisan:

- artículos del blog
    
- enlaces internos
    
- secciones de documentación
    
- endpoints relacionados con APIs

En el artículo de **API Documentation** se menciona que el backend permite generar archivos relacionados con el estado del servidor.

Durante la exploración del backend se encuentra un endpoint que genera un **heap dump**.

Un **heap dump** es un archivo que contiene el estado de la memoria de una aplicación en ejecución.

El endpoint encontrado es:

http://verbal-sleep.picoctf.net:49980/heapdump

Al acceder a este endpoint se descarga un archivo grande con el volcado de memoria del servidor.

El archivo descargado contiene datos binarios, pero puede analizarse utilizando herramientas de línea de comandos.

Para buscar la flag se usa:

strings heapdump | grep pico

El comando `strings` extrae texto legible de archivos binarios.
**picoCTF{Pat!3nt_15_Th3_K3y_871ffa9a}**
## Notas
#### Heap Dump

Un **heap dump** es una captura de la memoria de una aplicación en un momento determinado. Estos archivos suelen utilizarse para depuración, pero pueden contener información sensible como:

- credenciales
    
- tokens
    
- sesiones
    
- claves API
    
- flags en retos CTF
Exponer este tipo de archivos públicamente constituye una **vulnerabilidad de seguridad**.
#### Vulnerabilidad demostrada

El reto muestra un caso de **exposición de información sensible** debido a una mala configuración del servidor que permite descargar archivos de memoria.

Este tipo de vulnerabilidad puede provocar filtraciones de datos confidenciales.
#### Herramientas utilizadas

- Navegador web
    
- Herramientas de desarrollador (DevTools)
    
- Terminal Linux
    
- `strings`
    
- `grep`
## Referencias
- picoCTF – plataforma educativa de retos de seguridad.
    
- OWASP – guía sobre exposición de información sensible en aplicaciones web.
    
- Oracle – documentación sobre **heap dumps** y análisis de memoria en aplicaciones Java.