## Sleuthkit Apprentice
## Descripcion
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/137/disk.flag.img.gz)
## Solucion
- Descomprimimos la imagen del reto, vemos el tipo de archivo (como en los retos anteriores) para darnos cuenta que es nuevamente una imagen de disco.
- Vemos las particiones en el archivo de imagen de disco con `mmls`:

`mmls disk.flag.img`

- Listamos los archivos de la primer partición de Linux con `fls` :

`fls -o 2048 disk.flag.img` 

- Al no encontrar nada cambiamos de partición y hacemos un listado recursivo:

`fls -o 360448 -r disk.flag.img`

- Visualizamos el archivo que contiene la bandera en base a su offset con `icat`:

`icat  -o 360448 -r disk.flag.img 2371`

**picoCTF{by73_5urf3r_adac6cb4}**
## Notas

#### Análisis de imágenes de disco

- Imagen de disco  
    Representación exacta de un sistema de almacenamiento.
#### Particiones múltiples

- Partición de disco  
    Un disco puede contener varias particiones independientes.
#### Análisis forense digital

- Análisis forense digital  
    Incluye:
    - Identificación de particiones
    - Exploración de sistemas de archivos
    - Recuperación de evidencia
#### Inodos

- Identificadores internos de archivos en sistemas Linux.
- Necesarios para extraer archivos con herramientas forenses.
#### Codificación de caracteres

- UTF-8 vs UTF-16
- Importante cuando los datos no se visualizan correctamente.
#### Herramientas utilizadas
- The Sleuth Kit  
    Suite principal de análisis.
- mmls  
    Muestra particiones.
- fls  
    Lista archivos dentro del sistema de archivos.
- icat  
    Extrae archivos mediante inode.
- grep  
    Filtra resultados.
- iconv  
    Convierte codificaciones de texto.
## Referencias
- The Sleuth Kit  
    [https://www.sleuthkit.org/](https://www.sleuthkit.org/)
- fls  
    Documentación de listado de archivos.
- icat  
    Documentación de extracción de archivos.
- picoCTF  
    [https://picoctf.org/](https://picoctf.org/)