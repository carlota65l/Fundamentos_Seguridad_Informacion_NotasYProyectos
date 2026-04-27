## substitution2
## Descripcion
It seems that another encrypted message has been intercepted. The encryptor seems to have learned their lesson though and now there isn't any punctuation! Can you still crack the cipher?Download the message [here](https://artifacts.picoctf.net/c/112/message.txt).
## Solucion

**picoCTF{N6R4M_4N41Y515_15_73D10U5_8E1BF808}**
## Notas
- **Patristocrat vs. Aristocrat:** En la jerga criptográfica, a un cifrado de sustitución que conserva sus espacios y signos de puntuación se le llama _Aristocrat_. Cuando se eliminan todos los espacios (como en este ejercicio) o se agrupan las letras en bloques fijos de 5 caracteres, el cifrado se denomina _Patristocrat_. Históricamente, los militares hacían esto para destruir los patrones de longitud de las palabras.
    
- **Análisis de N-Gramas:** Un N-grama es una secuencia continua de caracteres. Como no puedes buscar palabras de 2 o 3 letras, buscas secuencias que se repiten estadísticamente en el idioma inglés:
    
    - **Bigramas (2 letras):** Los más comunes son TH, HE, IN, ER, AN.
        
    - **Trigramas (3 letras):** El rey indiscutible es THE, seguido de AND, ING, ENT.
        
    - **Cuadrigramas (4 letras):** TION, NENT, THAT.
## Referencias
https://guballa.de/substitution-solver