##  la cifra de
## Descripcion

I found this cipher in an old book.Can you figure out what it says? Connect with nc fickle-tempest.picoctf.net 63043.
## Solucion
Si nos enfocamos directamente en la última parte del mensaje, que es donde se encuentra la flag cifrada: `hgqqpohzCZK{m311a50_0x_a1rn3x3_h1ah3xgn3a3Gj6}`

El patrón de la clave cíclica (`f-l-a-g`) en este punto exacto del texto se alinea como la secuencia `a-g-f-l`. Al restar los valores numéricos de estas letras al texto cifrado, ocurre la magia:

- `hgqqpohz` + (clave) ➔ **`...half`**
    
- `pohzCZK` + (clave `a-g-f-l-a-g-f`) ➔ **`picoCTF`**
    
- `m` - `l` ➔ **`b`**
    
- `311` (se ignoran) ➔ **`311`**
    
- `a` - `a` ➔ **`a`**
    
- `50_0` (se ignoran) ➔ **`50_0`**
    
- `x` - `g` ➔ **`r`**
    
- `_` (se ignora) ➔ **`_`**
    
- `a` - `f` ➔ **`v`**
    
- ...y así sucesivamente.

picoCTF{b311a50_0r_v1gn3r3_c1ph3rbc3a3Ae6}
## Notas
Cifrado de Vigenère: Es un método de cifrado por sustitución simple polialfabética. Utiliza una serie de diferentes cifrados César basados en las letras de una palabra clave.

• Giovan Battista Bellaso: Aunque el cifrado lleva el nombre de Blaise de Vigenère, Bellaso fue quien lo describió primero en 1553 en su libro "La cifra del Sig. Giovan Battista Bellaso".

• Tabula Recta: La matriz de 26x26 letras utilizada tradicionalmente para cifrar y descifrar este algoritmo de forma manual.
## Referencias
CyberChef: Usar la operación "Vigenere Decode".


  • [dCode.fr](http://dcode.fr/): Excelente para ataques de fuerza bruta si no se conoce la clave.
  
  • Guballa Vigenère Solver: Útil para descifrar automáticamente basándose en análisis estadístico del lenguaje..


• Análisis de Frecuencia: A diferencia del cifrado César, Vigenère es resistente al análisis de frecuencia directo, requiriendo métodos como el Examen de Kasiski.