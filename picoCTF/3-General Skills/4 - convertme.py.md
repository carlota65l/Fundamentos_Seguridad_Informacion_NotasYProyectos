##  convertme.py
## Descripcion

Run the Python script and convert the given number from decimal to binary to get the flag.[Download Python script](https://artifacts.picoctf.net/c/23/convertme.py)

## Solucion
### solucion 1_ usando python


El script genera un número decimal aleatorio y solicita su conversión a binario. Para resolver el ejercicio, es necesario comprender el funcionamiento de los sistemas numéricos y utilizar herramientas manuales o automatizadas para realizar la conversión correctamente. Una vez ingresada la respuesta correcta, el script valida el resultado y muestra la flag como evidencia de éxito.

```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/23/convertme.py
--2026-02-16 18:25:12--  https://artifacts.picoctf.net/c/23/convertme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.43, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1189 (1.2K) [application/octet-stream]
Saving to: 'convertme.py'

convertme.py            100%[=============================>]   1.16K  --.-KB/s    in 0s      

2026-02-16 18:25:12 (75.7 MB/s) - 'convertme.py' saved [1189/1189]

BelovedCis-picoctf@webshell:~$ ls
README.txt  convertme.py
BelovedCis-picoctf@webshell:~$ python3 convertme.py
If 60 is in decimal base, what is it in binary base?
Answer: 111100
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_9c3b7d4d}
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{4ll_y0ur_b4535_9c3b7d4d}

## Notas

- El sistema decimal es un sistema de numeración en base 10 que utiliza los dígitos del 0 al 9.
- El sistema binario es un sistema de numeración en base 2 que utiliza únicamente los dígitos 0 y 1.
- Las computadoras utilizan el sistema binario como base para representar y procesar la información.
- Python permite convertir números decimales a binarios utilizando funciones integradas como:
`bin(numero)`

- El comando **python3** se utiliza para ejecutar scripts escritos en Python versión 3.
- La entrada de datos en la terminal permite interactuar directamente con los programas.
## Referencias

picoCTF. Plataforma educativa de ciberseguridad.

Python Software Foundation. Documentación oficial del lenguaje Python. [https://www.python.org](https://www.python.org)

GCHQ. CyberChef. Herramienta de análisis y conversión de datos. [https://gchq.github.io/CyberChef/](https://gchq.github.io/CyberChef/)

Stallings, W. (2017). Network Security Essentials: Applications and Standards. Pearson.

Shotts, W. E. (2019). The Linux Command Line. No Starch Press.

Documentación oficial de sistemas Linux. Manejo de scripts y comandos en terminal.