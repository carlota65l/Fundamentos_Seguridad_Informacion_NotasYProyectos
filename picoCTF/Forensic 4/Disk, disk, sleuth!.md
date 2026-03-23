## Disk, disk, sleuth!
## Descripcion


## Solucion
- Descomprimir el archivo del reto:

 `gzip -d dds1-alpine.flag.img.gz` 

- Examinamos el tipo de archivo, es una imagen de disco:

`file dds1-alpine.flag.img`

- Instalar `sleuthkit` , herramienta para análisis forense:

`sudo apt install -y sleuthkit`

- Buscar cadenas dentro de la imagen de disco con `srch_strings` y obtenemos la bandera:

`srch_strings dds1-alpine.flag.img | grep pico`

**picoCTF{f0r3ns1c4t0r_n30phyt3_5e56e786}**
## Notas

#### Análisis forense digital

- Análisis forense digital  
    Disciplina que se enfoca en recuperar y analizar información de dispositivos digitales.
#### Imagen de disco

- Imagen de disco  
    Copia exacta de un dispositivo de almacenamiento.

#### Strings en binarios

- Técnica básica:
    - Buscar texto legible dentro de archivos binarios.
- Útil cuando:
    - Los datos no están cifrados.
    - La flag está en texto plano.
## Referencias
- The Sleuth Kit  
    [https://www.sleuthkit.org/](https://www.sleuthkit.org/)
- picoCTF  
    [https://picoctf.org/](https://picoctf.org/)
- Análisis forense digital  
    Conceptos de recuperación de evidencia en sistemas digitales.