## substitution0
## Descripcion
A message has come in but it seems to be all scrambled. Luckily it seems to have the key at the beginning. Can you crack this substitution cipher?Download the message [here](https://artifacts.picoctf.net/c/153/message.txt).
## Solucion
La primera línea  (`OHNFUMWSVZLXEGCPTAJDYIRKQB`) es nuestro mapa. Para descifrarlo, solo tuvimos que alinear esa clave con el abecedario estándar. La posición de cada letra en tu clave corresponde a una letra en el abecedario normal:

- **Clave:** `O H N F U M W S V Z L X E G C P T A J D Y I R K Q B`
    
- **Real:** `A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`
    

Si aplicamos esta regla a la parte de la flag `5YH5717Y710G_3I0XY710G_03055505` (los números se mantienen igual):

- **Y** = U
    
- **H** = B
    
- **G** = N
    
- **I** = V
    
- **X** = L

**PICOCTF{5UB5717U710N_3V0LU710N_03055505}**
## Notas
An alphabetic substitution is a substitution cipher where the letters of the alphabet are replaced by others according to a 1-1 correspondence (a plain letter always corresponds to the same cipher letter).

The substitution is said to be monoalphabetic because it uses only one alphabet, this alphabet is said to be disordered.
## Referencias
https://www.dcode.fr/monoalphabetic-substitution