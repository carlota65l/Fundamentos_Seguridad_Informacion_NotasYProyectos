## Codebook
## Descripcion

Run the Python script `code.py` in the same directory as `codebook.txt`.

- [Download code.py](https://artifacts.picoctf.net/c/1/code.py)
- [Download codebook.txt](https://artifacts.picoctf.net/c/1/codebook.txt)


descargar y ejecutar un script escrito en el lenguaje de programación Python, el cual depende de un archivo adicional denominado **codebook.txt** para funcionar correctamente. Esta actividad fue realizada en el entorno de práctica de la plataforma picoCTF, cuyo propósito es enseñar conceptos fundamentales de programación, análisis de archivos y ejecución de scripts en entornos de línea de comandos.

El archivo principal, **code.py**, contiene instrucciones programadas que leen información desde el archivo **codebook.txt**, el cual actúa como fuente de datos o referencia. Al ejecutar el script en el mismo directorio donde se encuentra el archivo de texto, el programa procesa la información y muestra la flag correspondiente.

## Solucion
### solucion 1_ usando python

Se accedió a una terminal o entorno de línea de comandos proporcionado por la plataforma.
 
```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/1/code.py
--2026-02-16 18:15:27--  https://artifacts.picoctf.net/c/1/code.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.128, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1278 (1.2K) [application/octet-stream]
Saving to: 'code.py'

code.py                 100%[=============================>]   1.25K  --.-KB/s    in 0s      

2026-02-16 18:15:27 (331 MB/s) - 'code.py' saved [1278/1278]

BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/1/codebook.txt
--2026-02-16 18:15:32--  https://artifacts.picoctf.net/c/1/codebook.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.128, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27 [application/octet-stream]
Saving to: 'codebook.txt'

codebook.txt            100%[=============================>]      27  --.-KB/s    in 0s      

2026-02-16 18:15:33 (7.09 MB/s) - 'codebook.txt' saved [27/27]

BelovedCis-picoctf@webshell:~$ ls
Addadshashanammu      README.txt     big-zip-files.zip  codebook.txt  files      runme.py
Addadshashanammu.zip  big-zip-files  code.py            enc_flag      files.zip
BelovedCis-picoctf@webshell:~$ python3 code.py
picoCTF{c0d3b00k_455157_d9aa2df2}
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{c0d3b00k_455157_d9aa2df2}


La ejecución de scripts que dependen de archivos externos es una práctica común en el desarrollo de software y en el análisis de sistemas informáticos. Este ejercicio permitió comprender la importancia de la estructura de archivos, el uso del intérprete de Python y la interacción entre programas y archivos de datos.

## Notas

- Python es un lenguaje de programación interpretado que permite ejecutar instrucciones directamente mediante un intérprete.
- Los scripts pueden depender de archivos externos para obtener información necesaria para su ejecución.
- El archivo **codebook.txt** funciona como una fuente de datos que el script utiliza para completar su operación.
- El comando **wget** permite descargar archivos desde internet mediante una dirección URL.
- El comando **python3** se utiliza para ejecutar scripts escritos en Python versión 3.
- Ambos archivos deben estar en el mismo directorio para que el script pueda acceder correctamente al archivo de datos.

Importancia en ciberseguridad:

Este tipo de ejercicios es relevante porque enseña cómo:

- Analizar scripts que dependen de archivos externos
- Comprender la relación entre programas y archivos de configuración
- Ejecutar herramientas automatizadas
- Analizar el comportamiento de programas desconocidos
- Recuperar información mediante el análisis de scripts

Estas habilidades son fundamentales para el análisis forense digital, pruebas de penetración y análisis de malware.
## Referencias

picoCTF. Plataforma educativa de ciberseguridad.

Python Software Foundation. Documentación oficial del lenguaje Python.

Stallings, W. (2017). Network Security Essentials: Applications and Standards. Pearson.

Shotts, W. E. (2019). The Linux Command Line. No Starch Press.

Documentación oficial de Linux. Uso de comandos wget, python3, ls y manejo de archivos.