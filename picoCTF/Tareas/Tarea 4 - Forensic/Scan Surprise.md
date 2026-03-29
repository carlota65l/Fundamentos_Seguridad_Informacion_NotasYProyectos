## Scan Surprise
## Descripcion
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/13/challenge.zip)

The same files are accessible via SSH here:`ssh -p 56095 ctf-player@atlas.picoctf.net`Using the password `f3b61b38`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
## Solucion

- **Conexión Remota:** Se estableció una sesión cifrada vía SSH para acceder al entorno del reto.
    
- **Exploración del Sistema:** Uso del comando `ls` para identificar la ubicación del archivo `flag.png` dentro del directorio `drop-in/`.
    
- **Procesamiento de Imagen:** * _Opción A (Línea de comandos):_ Empleo de la herramienta `zbarimg` (paquete `zbar-tools`) para decodificar el QR directamente en la terminal.
    
    - _Opción B (Análisis Visual):_ Descarga del archivo mediante `scp` o enlace directo para escaneo mediante un dispositivo móvil o lector web.
        
- **Extracción del Resultado:** El software de escaneo traduce los patrones visuales del QR a la cadena de texto con el formato `picoCTF{...}`.

**picoCTF{p33k_@_b00_d4ca652e}**
## Notas

- **OpenSSH:** Cliente para acceso remoto.
    
- **ZBar-tools (zbarimg):** Suite de software de código abierto para leer códigos de barras y QR desde archivos de imagen.
    
- **Unzip:** Utilidad para extraer los archivos del desafío localmente.
## Referencias

- **ZBar Bar Code Reader Documentation:** "Scanning images using the command line". Disponible en: [http://zbar.sourceforge.net/](http://zbar.sourceforge.net/)
    
- **ISO/IEC 18004:** Estándar internacional para la simbología de códigos QR (Quick Response Code).
    
- **Linux Manual Pages (man pages):** Comandos `ssh(1)`, `ls(1)` y `cd(1)`.