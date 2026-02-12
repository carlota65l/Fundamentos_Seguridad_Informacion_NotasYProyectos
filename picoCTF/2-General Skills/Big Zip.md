## Big Zip
## Descripcion
Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/505/big-zip-files.zip)
## Solucion
### solucion 1_ usando python


La forma más práctica de encontrar el flag dentro de miles de archivos es usando `grep` para buscar la cadena típica de picoCTF:
Esto le dice a `grep` que busque recursivamente (con `-r`) dentro de todos los archivos y subcarpetas.
 
```bash
BelovedCis-picoctf@webshell:~$ grep -r "picoCTF" big-zip-files/
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}

```

Respuesta: picoCTF{gr3p_15_m4g1c_ef8790dc}

## Notas

## Conceptos clave utilizados

- **Compresión de archivos (.zip)**  
    Método para reducir el tamaño de archivos y agrupar múltiples archivos en uno solo.
    
- **Búsqueda recursiva**  
    Técnica para buscar dentro de todos los subdirectorios automáticamente.
    
- **Expresiones de búsqueda**  
    Uso de patrones de texto específicos para localizar información.
    
- **Herramientas de línea de comandos**  
    Permiten automatizar tareas y trabajar eficientemente con grandes volúmenes de datos.

### Aprendizajes obtenidos

- La línea de comandos es más eficiente que la búsqueda manual cuando existen miles de archivos.
    
- `grep` es una herramienta fundamental en ciberseguridad y análisis forense.
    
- En CTFs, reconocer patrones comunes (como el formato del flag) facilita la resolución.
## Referencias
- GNU Project. (s.f.). _GNU Grep Manual_.
    
- Info-ZIP. (s.f.). _UnZip Manual Page_.
    
- picoCTF. (s.f.). _picoCTF Platform and Challenges_. Carnegie Mellon University.
    
- Shotts, W. (2019). _The Linux Command Line: A Complete Introduction_. No Starch Press.
    
- Barrett, D. (2016). _Linux Pocket Guide_. O’Reilly Media.