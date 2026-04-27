##  substitution1
## Descripcion
A second message has come in the mail, and it seems almost identical to the first one. Maybe the same thing will work again.Download the message [here](https://artifacts.picoctf.net/c/183/message.txt).
## Solucion

Sustituyendo los valores que encontramos (los números se quedan igual):

- `OE3AH3ULY` -> **FR3QU3NCY** (Frecuency)
    
- `4774LI5` -> **4774CK5** (Attacks)
    
- `4E3` -> **4R3** (Are)
    
- `L001` -> **C001** (Cool, escrito con un 1 al final)
    
- `6J0659OM` -> **6E0659FB**
    

El texto plano completo es una introducción de qué son las competencias de ciberseguridad, y la flag es un guiño directo al método que acabamos de usar: los ataques de frecuencia son geniales (_Frequency attacks are cool_).

**picoCTF{FR3QU3NCY_4774CK5_4R3_C001_6E0659FB}**
## Notas
- **Cifrado de Sustitución Monoalfabética:** Es el método criptográfico que acabas de vencer. Consiste en reemplazar cada letra del alfabeto original por otra letra fija. A diferencia del cifrado César (que solo desplaza las letras un número de posiciones), aquí el alfabeto está completamente revuelto, creando $26!$ (más de $4 \times 10^{26}$) claves posibles.
    
- **Análisis de Frecuencias:** Es la vulnerabilidad principal de la sustitución monoalfabética. En inglés, la letra 'E' aparece en un 12.7% de los textos, seguida por la 'T' y la 'A'. Si en un texto cifrado la letra 'X' es la que más se repite, es altamente probable que represente a la 'E'.
    
- **Ataque de Texto Plano Conocido (KPA):** Es la técnica que usamos al buscar `picoCTF{` y la palabra `CTF`. Ocurre cuando el atacante tiene acceso tanto al texto cifrado como a una parte (por pequeña que sea) del texto original.
    
- **Identificación de Patrones:** Las palabras cortas son las mayores delatoras en el idioma inglés. Palabras de una letra suelen ser 'A' o 'I'. Las de tres letras más comunes son 'THE' y 'AND'.
## Referencias
https://quipqiup.com/