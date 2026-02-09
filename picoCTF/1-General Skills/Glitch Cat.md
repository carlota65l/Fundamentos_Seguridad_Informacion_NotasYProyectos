## Glitch Cat
## Descripcion

**Our flag printing service has started glitching!**
nc saturn.picoctf.net 64297


## Solucion
### solucion 1_ usando python


 -Los valores estan expresados en **hexadecimal**, por lo que primero se interpretan en base 16.

 
```bash
BelovedCis-picoctf@webshell:~$ nc saturn.picoctf.net 64297
'picoCTF{gl17ch_m3_n07_' + chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64) + '}'
```
|Hexadecimal|Decimal|ASCII|
0x39                          57             9
0x63                          99             c
0x34                          52             4
0x32                          50             2
0x61                          97             a
0x34                          52             4
0x35                          53             5
0x64                        100            d

Respuesta: **9c42a45d**

picoCTF{gl17ch_m3_n07_9c42a45d}

## Notas
- Este reto utiliza una técnica común en CTFs para ocultar información sensible.
    
- La función `chr()` en Python convierte **valores ASCII numéricos a caracteres legibles**
    
    
- El servicio `nc` (netcat) se usó para **interactuar con un proceso remoto**, típico en retos de tipo _pwn_ o _reverse_.
    
- Reconocer patrones como `picoCTF{` o `chr(0xNN)` puede acelerar el resultado.

## Referencias
ASCII Table: [https://www.asciitable.com](https://www.asciitable.com)