## First Find
## Descripcion
Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/502/files.zip)
## Solucion
### solucion 1_ usando python


descargar un archivo comprimido en formato `.zip` que contiene múltiples carpetas y subdirectorios.
 
```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/502/files.zip
--2026-02-12 02:11:55--  https://artifacts.picoctf.net/c/502/files.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.170.131.33, 3.170.131.72, 3.170.131.77, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.170.131.33|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3995553 (3.8M) [application/octet-stream]
Saving to: 'files.zip'

files.zip             100%[=========================>]   3.81M  1.83MB/s    in 2.1s    

2026-02-12 02:11:57 (1.83 MB/s) - 'files.zip' saved [3995553/3995553]

BelovedCis-picoctf@webshell:~$ unzip files.zip
Archive:  files.zip
   creating: files/
   creating: files/satisfactory_books/
   creating: files/satisfactory_books/more_books/
  inflating: files/satisfactory_books/more_books/37121.txt.utf-8  
  inflating: files/satisfactory_books/23765.txt.utf-8  
  inflating: files/satisfactory_books/16021.txt.utf-8  
  inflating: files/13771.txt.utf-8   
   creating: files/adequate_books/
   creating: files/adequate_books/more_books/
   creating: files/adequate_books/more_books/.secret/
   creating: files/adequate_books/more_books/.secret/deeper_secrets/
   creating: files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/
 extracting: files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt  
  inflating: files/adequate_books/more_books/1023.txt.utf-8  
  inflating: files/adequate_books/46804-0.txt  
  inflating: files/adequate_books/44578.txt.utf-8  
   creating: files/acceptable_books/
   creating: files/acceptable_books/more_books/
  inflating: files/acceptable_books/more_books/40723.txt.utf-8  
  inflating: files/acceptable_books/17880.txt.utf-8  
  inflating: files/acceptable_books/17879.txt.utf-8  
  inflating: files/14789.txt.utf-8   
BelovedCis-picoctf@webshell:~$ find . -name "uber-secret.txt"
./files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
BelovedCis-picoctf@webshell:~$ cat ./files/adequate_books/more_books/.secret/deeper_secr
ets/deepest_secrets/uber-secret.txt
picoCTF{f1nd_15_f457_ab443fd1}
BelovedCis-picoctf@webshell:~$ 

```

Respuesta: picoCTF{f1nd_15_f457_ab443fd1}

## Notas

 Objetivo técnico

- Descomprimir archivos comprimidos.
    
- Navegar estructuras de directorios anidados.
    
- Buscar archivos por nombre de forma eficiente.
    
- Aplicar comandos de terminal para optimizar tareas.

### Compresión de archivos

Los archivos `.zip` permiten agrupar y reducir el tamaño de múltiples archivos en uno solo.

###  Búsqueda recursiva

Permite buscar dentro de todos los subdirectorios automáticamente sin necesidad de inspeccionar carpeta por carpeta.

###  Herramientas de línea de comandos

Comandos como `unzip`, `find` y `cat` son herramientas esenciales para el manejo eficiente de archivos en entornos Linux/Unix.

###  Sistemas de archivos jerárquicos

Los sistemas operativos organizan archivos en estructuras de árbol, lo que hace necesario el uso de herramientas automatizadas para búsquedas extensas.

### Aprendizajes obtenidos

- La línea de comandos permite realizar búsquedas más rápidas que la exploración manual.
    
- El comando `find` es fundamental para localizar archivos en estructuras grandes.
    
- Las habilidades básicas de administración de archivos son esenciales en ciberseguridad.
    
- La automatización mejora la eficiencia en análisis forense y resolución de retos CTF.
## Referencias
- GNU Project. (s.f.). _GNU Find Utilities Manual_. Free Software Foundation.
    
- GNU Project. (s.f.). _UnZip Manual_. Free Software Foundation.
    
- picoCTF. (s.f.). _picoCTF General Skills Challenges_. Carnegie Mellon University.
    
- Shotts, W. E. (2019). _The Linux Command Line: A Complete Introduction_ (2nd ed.). No Starch Press.
    
- Nemeth, E., Snyder, G., Hein, T., & Whaley, B. (2017). _UNIX and Linux System Administration Handbook_ (5th ed.). Pearson.