## Forensics Git 1
## Descripcion
Can you find the flag in this disk image?Download the disk image [here](https://challenge-files.picoctf.net/c_plain_mesa/4538dd1f2e93e907c17f0b663c0e1fae2d7054a72b4ee36977f20cfbf3b0a01c/disk.img.gz).

El reto consiste en analizar una imagen de disco para recuperar una bandera (flag) que fue eliminada. Para resolverlo, se requiere realizar un análisis forense del sistema de archivos y examinar el historial de versiones de un repositorio Git presente dentro de la imagen.
## Solucion
Se descargó la imagen de disco comprimida y se descomprimió para obtener el archivo `disk.img`.

Herramienta utilizada:

- `gunzip`

Para determinar la estructura de la imagen se utilizó la herramienta `mmls`, perteneciente al **The Sleuth Kit**, que permite visualizar la tabla de particiones.

Esta herramienta mostró varias particiones Linux dentro del disco.

Se calculó el **offset** multiplicando el sector inicial de la partición por el tamaño del sector (512 bytes).

Después se montó la partición utilizando el comando:

`mount -o loop,offset=<offset> disk.img disk`

Esto permitió acceder al sistema de archivos contenido dentro de la imagen.

Una vez montada la partición, se exploraron los directorios del sistema para encontrar archivos relevantes.

Se identificó un repositorio Git en:

`/home/ctf-player/Code/secrets/.git`

El repositorio fue analizado usando comandos de Git para revisar el historial de cambios.

Comandos utilizados:

- `git log`
    
- `git show`
    
- `git log -p`
    

Estos comandos permiten visualizar:

- commits anteriores
    
- cambios en archivos
    
- información eliminada en versiones recientes.

Al revisar los commits anteriores se pudo recuperar la flag que había sido eliminada en una versión posterior del repositorio.
Esto demuestra que **Git conserva todo el historial de modificaciones**, incluso si un archivo es eliminado posteriormente.

**picoCTF{g17_r3m3mb3r5_d4ddf904}**
## Notas

Durante la resolución del reto se aplicaron los siguientes conceptos:

- análisis forense de imágenes de disco
    
- identificación de particiones
    
- montaje de sistemas de archivos
    
- exploración de directorios en Linux
    
- recuperación de información en repositorios Git
    
- análisis de historial de versiones
También se comprendió que la eliminación de información en sistemas de control de versiones no implica su desaparición total, ya que las versiones anteriores permanecen almacenadas.
## Referencias
- Git. (2024). _Git Documentation_. [https://git-scm.com/docs](https://git-scm.com/docs)
- The Sleuth Kit. (2024). _Sleuth Kit Documentation_. [https://www.sleuthkit.org](https://www.sleuthkit.org)
- picoCTF. (2024). _picoCTF Official Platform_. [https://picoctf.org](https://picoctf.org)
- Casey, E. (2011). _Digital Evidence and Computer Crime_. Academic Press.
- Carrier, B. (2005). _File System Forensic Analysis_. Addison-Wesley.