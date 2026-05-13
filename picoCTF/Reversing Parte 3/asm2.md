## asm2
## Descripcion
What does asm2(0xf,0x17) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://challenge-files.picoctf.net/c_fickle_tempest/111d025d4750385ea525035ae7b10ebb3c4518f39726f774aa34c8523e52329e/test.S)
## Solucion

### 1. Lectura de Argumentos y Variables Locales

La convención de llamadas en x86 (32 bits) coloca los argumentos en la pila por encima del registro base (`ebp`).
- `[ebp+0x8]`: Primer argumento = **`0xf`** (15 en decimal).
- `[ebp+0xc]`: Segundo argumento = **`0x17`** (23 en decimal).

Las líneas `<+10>` a `<+19>` toman estos argumentos y los guardan en variables locales (por debajo de `ebp`):
- `[ebp-0x4]` (llamémosla `var1`) se inicializa con el segundo argumento: **`0x17`** (23).
- `[ebp-0x8]` (llamémosla `var2`) se inicializa con el primer argumento: **`0xf`** (15).

### 2. Estructura del Bucle (Loop)

La instrucción en `<+22>` (`jmp 0x11d0`) hace un salto incondicional a la comprobación del bucle en `<+35>`.
Podemos traducir este código a un bucle `while` simple en Python o C:
Python

```
var1 = 0x17 # 23
var2 = 0xf  # 15

while var2 <= 0xd72d:  # 0xd72d es 55085 en decimal
    var1 += 0x1        # Suma 1
    var2 += 0xcb       # Suma 203 en decimal
    
return var1
```
### 3. Cálculo de las Iteraciones

Para saber qué retorna sin tener que simular el código 200 veces, calculamos cuántas iteraciones tomará romper la condición del ciclo:

- `var2` comienza en **15**.
- Queremos saber en qué iteración `var2` superará **55085**.
- En cada iteración, `var2` aumenta en **203**.
Distancia a cubrir: 55085 - 15 = **55070**
Número de iteraciones necesarias: 55070 / 203 = **271.28**
Dado que el bucle continúa mientras sea menor o _igual_, después de 271 iteraciones exactas el valor será menor al límite, por lo que el ciclo correrá una vez más. El bucle se ejecutará un total de **272 veces**.

### 4. Resultado Final

Como el bucle se ejecuta 272 veces, y `var1` incrementa de 1 en 1, simplemente sumamos eso al valor inicial de `var1`:

- Valor inicial de `var1` = 23
- Valor final = 23 + 272 = **295**
Para enviar tu flag en el formato solicitado, convertimos el 295 decimal a hexadecimal:
- 295 en Hexadecimal = **`0x127`**
**Flag: 0x127**
## Notas

## Referencias
