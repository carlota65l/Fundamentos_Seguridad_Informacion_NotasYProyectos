## the numbers
## Descripcion
The numbers... what do they mean?[numbers.png](https://challenge-files.picoctf.net/c_fickle_tempest/7b39deba4212c233b1628c93f16639ed02ad90f51436d2a8914bb11f74a982d3/the_numbers.png)

## Solucion
Es un cifrado tipo **A1Z26** (donde A=1, B=2, ..., Z=26).

Decodificando:

- 16 9 3 15 3 20 6 → **P I C O C T F** → `picoctf`
- Dentro de llaves:
    - 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14  
        → **T H E N U M B E R S M A S O N** → `thenumbersmason`

✅ **Flag final:**

**picoctf{thenumbersmason}**
## Notas
Forma 1 - Manual,
Buscar en google : alphabet numbered,
Ir decodificando cada número de acuerdo al alfabeto numerado,
Forma 2 - Cybercgef,
Ir a cyberchef, elegir la receta : a1z26,
Forma3 - Python - IA,
Pedir a Gemini o Chatgpt: Crea un script sencillo en python para recodificar una cadena de numeros en a1z26 que se pase como parametro
## Referencias
https://gchq.github.io/CyberChef/
