## DISKO 4
## Descripcion
Can you find the flag in this disk image? This time I deleted the file! Let see you get it now!Download the disk image [here](https://challenge-files.picoctf.net/c_plain_mesa/6d54c5d858c8e5a8aaac625fe13dec0404bf14287dcbff8510e934958ab5ed82/disko-4.dd.gz).

El reto consistía en encontrar una **flag oculta dentro de una imagen de disco** llamada `disko-4.dd.gz`.  
El enunciado indicaba que el archivo que contenía la flag había sido **eliminado**, por lo que el objetivo era **recuperar archivos borrados del sistema de archivos**.
## Solucion

El archivo descargado estaba comprimido en formato **gzip**, por lo que primero fue necesario descomprimirlo.

`gunzip disko-4.dd.gz`

Esto generó el archivo:

`disko-4.dd`

Se utilizó la herramienta **fls** de **The Sleuth Kit** para listar los archivos del sistema de archivos, incluyendo los eliminados.

`fls -r -d disko-4.dd`

Opciones utilizadas:

- `-r` → búsqueda recursiva
    
- `-d` → mostrar archivos eliminados
    

Resultado:

`r/r * 522629: log/messages r/r * 532021: log/dont-delete.gz`

El símbolo `*` indica que el archivo fue **eliminado del sistema de archivos**, pero aún puede recuperarse si los bloques de datos no han sido sobrescritos.

Para recuperar el contenido del archivo eliminado se utilizó **icat**, que permite extraer archivos a partir de su **inode**.

`icat disko-4.dd 532021 > dont-delete.gz`

El archivo recuperado estaba comprimido, por lo que se descomprimió usando **gunzip**.

`gunzip dont-delete.gz`

Esto generó el archivo:

`dont-delete`

Finalmente, se visualizó el contenido del archivo:

`cat dont-delete`
picoCTF{d3l_d0n7_h1d3_w3ll_fe34c2cb}

## Notas

Cuando un archivo se elimina en un sistema de archivos, normalmente **los datos no se borran inmediatamente**, sino que el sistema solo marca el espacio como disponible. Esto permite recuperar archivos eliminados utilizando herramientas forenses.

#### Inodes

Un **inode** es una estructura de datos que almacena información sobre un archivo, como:

- ubicación de los bloques de datos
- permisos
- tamaño
- propietario
Herramientas como `icat` utilizan el inode para recuperar el contenido del archivo.

#### The Sleuth Kit

**The Sleuth Kit (TSK)** es un conjunto de herramientas de código abierto utilizado en análisis forense digital para examinar sistemas de archivos y recuperar evidencia.
## Referencias
- Kali Linux
- The Sleuth Kit
    
    - `fls`
        
    - `icat`
        
- `gunzip`
    
- `cat`