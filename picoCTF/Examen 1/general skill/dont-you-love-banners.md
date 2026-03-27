## dont-you-love-banners

## Descripcion
Can you abuse the banner?The server has been leaking some crucial information on `tethys.picoctf.net 59510`. Use the leaked information to get to the server.To connect to the running application use `nc tethys.picoctf.net 60294`. From the above information abuse the machine and find the flag in the /root directory
## Solucion
- `nc <ip o dominio> <puerto>`: Conecta a un puerto TCP crudo. Útil para interactuar con servicios personalizados o capturar banners.
    
- `ls -la`: Lista todos los archivos (incluso los ocultos) mostrando sus permisos y dueños.
    
- `mv <archivo1> <archivo2>`: Mueve o renombra un archivo.
    
- `ln -s <ruta_al_archivo_objetivo> <nombre_del_enlace>`: Crea un Enlace Simbólico (Symlink). Es la herramienta clave para este tipo de ataques de lectura arbitraria.

**picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_ed6f9c71}**

## Notas
#### Fuga de Información (Information Leak / Banner Grabbing)

- **Concepto:** Los "banners" son mensajes de texto que los servidores envían automáticamente cuando te conectas a ellos (por ejemplo, para mostrar la versión del software de SSH o FTP). Si están mal configurados, pueden revelar información sensible.
    
- **Vulnerabilidad:** En este reto, el administrador dejó una contraseña (`My_Passw@rd_@1234`) escrita por error en el banner del puerto 59510. Esto se conoce como _Information Disclosure_ (CWE-200).
    
- **Herramienta:** `nc <host> <puerto>` (Netcat) es ideal para leer estos mensajes en crudo.
    

#### 2. Cultura Hacker y Phreaking

Los CTFs a menudo incluyen trivia para probar tu conocimiento general del mundillo:

- **DEFCON:** Es la conferencia anual de hackers más grande y antigua del mundo, celebrada en Las Vegas.
    
- **Phreaking:** Es el precursor del hacking informático, pero enfocado en manipular la red telefónica.
    
- **John Draper (Captain Crunch):** Es una figura histórica real. Descubrió que el silbato de juguete que venía en las cajas de cereales _Cap'n Crunch_ emitía un tono exacto de 2600 Hz. Ese tono era la señal maestra de la compañía telefónica AT&T, lo que le permitía hacer llamadas de larga distancia gratis.
    

#### 3. Escalada de Privilegios: Ataque de Enlace Simbólico (Symlink Attack)

- **El fallo del sistema:** El programa de bienvenida se ejecuta con permisos de Administrador (`root`) e imprime en pantalla el contenido de un archivo local llamado `banner`.
    
- **El Abuso:** Como el usuario de bajos privilegios (`player`) es dueño de la carpeta donde está ese archivo `banner`, puede borrarlo y reemplazarlo por un enlace simbólico (un acceso directo) que apunte a `/root/flag.txt`.
    
- **El resultado:** Cuando el programa de `root` se vuelve a ejecutar al abrir una nueva conexión, intenta leer su `banner`, sigue el acceso directo, y termina leyendo y mostrándote el archivo restringido sin darse cuenta.
    
- **Vulnerabilidad oficial:** _Improper Link Resolution Before File Access_ (CWE-59).
## Referencias
- **Sobre vulnerabilidades de Enlaces Simbólicos:** Busca en internet sobre **"Symlink attacks privilege escalation"**. Comprender cómo los programas con permisos elevados leen archivos locales es fundamental en seguridad Linux.
    
- **Catálogo CWE de MITRE:** Puedes buscar las vulnerabilidades **CWE-200** y **CWE-59** para leer documentación técnica y oficial sobre por qué ocurren estos fallos y cómo los desarrolladores los previenen.
    
- **Historia del Hacking:** Te recomiendo buscar documentales o artículos sobre "Phone Phreaking" y "The History of DEFCON". Te dará mucho contexto para futuros CTFs.