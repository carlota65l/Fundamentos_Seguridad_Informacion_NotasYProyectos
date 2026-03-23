## Sleuthkit Intro
## Descripcion

## Solucion
Descomprimir el archivo del reto igual que en el ejemplo anterior.,
gzip -d disk.img.gz 

Examinar el tipo de archivo, es una imagen de disco:,
file disk.img   

Vemos las particiones en la imgen de disco y su tamaño:,
mmls disk.img 

Conectamos al servidor del reto, el puerto puede variar, ahí responde la pregunta en base a la información obtenida anteriormente:,
nc saturn.picoctf.net 52273

**picoCTF{mm15_f7w!}**

## Notas

#### Tabla de particiones MBR

- Master Boot Record  
    Esquema tradicional que define cómo se organizan las particiones en un disco.

#### Particiones de disco

- Partición de disco  
    División lógica de un disco físico en secciones independientes.

#### Tipo de partición Linux (0x83)

- Identificador hexadecimal usado en MBR para sistemas Linux.
#### Análisis forense básico

- Análisis forense digital  
    Incluye:
    - Identificación de estructuras de disco
    - Interpretación de metadatos
#### Herramientas utilizadas

- gzip  
    Para descomprimir archivos.
- file  
    Identifica el tipo de archivo.
- The Sleuth Kit  
    Suite de análisis forense.
- mmls  
    Muestra la tabla de particiones de una imagen de disco.
- netcat  
    Permite interactuar con el servidor del reto (`nc`).
## Referencias
- The Sleuth Kit  
    [https://www.sleuthkit.org/](https://www.sleuthkit.org/)
- mmls  
    Documentación de análisis de particiones.
- Master Boot Record  
    Estructura clásica de particionado en discos.
- picoCTF  
    [https://picoctf.org/](https://picoctf.org/)