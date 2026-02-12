## - Tab, Tab, Attack
## Descripcion
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames.[Addadshashanammu.zip](https://challenge-files.picoctf.net/c_wily_courier/1d211441eced2214a10b0c2aacbf05d153aafcd6edc055f913cafcdb48a0b02b/Addadshashanammu.zip)

El objetivo es utilizar herramientas básicas de la terminal de Linux, especialmente **autocompletado con TAB**, para navegar eficientemente entre nombres largos y complejos hasta encontrar un archivo ejecutable que contiene el flag.
## Solucion
### solucion 1_ usando python


- - Uso eficiente de la terminal.
    
- Navegación en sistemas de archivos.
    
- Uso de comandos básicos de análisis como `strings`.
    
- Aplicación de búsqueda con `find`.
    

El archivo final encontrado (`fang-of-haynekhtnamet`) es un ejecutable ELF que contiene el flag oculto en texto plano dentro del binario.
```bash
BelovedCis-picoctf@webshell:~$ rm -rf Addadshashanammu Addadshashanammu.zip
BelovedCis-picoctf@webshell:~$ 
BelovedCis-picoctf@webshell:~$ ls
README.txt
BelovedCis-picoctf@webshell:~$ wget https://challenge-files.picoctf.net/c_wily_courier/1d211441eced2214a10b0c2aacbf05d153aafcd6edc055f913cafcdb48a0b02b/Addadshashanammu.zip
--2026-02-12 01:22:43--  https://challenge-files.picoctf.net/c_wily_courier/1d211441eced2214a10b0c2aacbf05d153aafcd6edc055f913cafcdb48a0b02b/Addadshashanammu.zip
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 3.160.5.18, 3.160.5.95, 3.160.5.64, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5166 (5.0K) [application/octet-stream]
Saving to: 'Addadshashanammu.zip'

Addadshashanammu.zip  100%[=========================>]   5.04K  --.-KB/s    in 0s      

2026-02-12 01:22:43 (46.8 MB/s) - 'Addadshashanammu.zip' saved [5166/5166]

BelovedCis-picoctf@webshell:~$ unzip Addadshashanammu.zip
Archive:  Addadshashanammu.zip
   creating: Addadshashanammu/
   creating: Addadshashanammu/Almurbalarammi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/
 extracting: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet.c  
  inflating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet  
BelovedCis-picoctf@webshell:~$ cd Addadshashanammu/
```

```bash
picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}
```

Respuesta: picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}

## Notas
- `rm -rf` elimina archivos permanentemente (usar con precaución).
    
- No se puede usar `cd` sobre un archivo, solo sobre directorios.
    
- `find` es útil cuando la estructura es muy profunda.
    
- Los ejecutables ELF pueden contener texto visible mediante `strings`.

## Referencias
- picoCTF – General Skills Challenges  
    [https://picoctf.org](https://picoctf.org)
    
- Manual de Linux – GNU Core Utilities  
    [https://www.gnu.org/software/coreutils/manual/](https://www.gnu.org/software/coreutils/manual/)
    
- Documentación del comando `strings`  
    [https://man7.org/linux/man-pages/man1/strings.1.html](https://man7.org/linux/man-pages/man1/strings.1.html)
    
- Documentación del comando `find`  
    [https://man7.org/linux/man-pages/man1/find.1.html](https://man7.org/linux/man-pages/man1/find.1.html)
    
- Bash Reference Manual  
    [https://www.gnu.org/software/bash/manual/](https://www.gnu.org/software/bash/manual/)