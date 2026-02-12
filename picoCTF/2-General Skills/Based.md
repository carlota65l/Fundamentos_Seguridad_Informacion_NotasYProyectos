## Based
## Descripcion
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337?

**Connect with nc fickle-tempest.picoctf.net 56633.**

## Solucion
### solucion 1_ usando python


- Identificar la base numérica.
    
- Convertir a decimal.
    
- Convertir decimal a ASCII.
    
- Unir los caracteres.
    
- Responder exactamente como pide el servidor.
 
```bash
BelovedCis-picoctf@webshell:~$ nc fickle-tempest.picoctf.net 56633
Let us see how data is stored
lime
Please give the 01101100 01101001 01101101 01100101 as a word.
...
you have 45 seconds.....

Input:
lime
Please give me the  o163 o157 o143 o153 o145 o164 as a word.
Input:
socket
Please give me the 636f6d7075746572 as a word.
Input:
computer
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_aa2bA794}
```

Respuesta: picoCTF{learning_about_converting_values_aa2bA794}

## Notas
El propósito del ejercicio es comprender cómo se representan los datos en distintos sistemas numéricos y cómo se transforman en texto usando el estándar ASCII.

Este tipo de retos evalúa:

- Comprensión de sistemas de numeración (base 2, 8, 10, 16)
    
- Conversión entre bases
    
- Interpretación de datos en ASCII
    
- Rapidez bajo presión (límite de tiempo)

 ### Python para Conversión

**Binario:**

`chr(int("01110011", 2))`

**Octal:**

`chr(int("163", 8))`

**Hexadecimal:**

`bytes.fromhex("63").decode()`

## Referencias
- Python Documentation – Built-in Functions  
    https://docs.python.org/3/library/functions.html#chr
    
- Python Documentation – bytes.fromhex()  
    https://docs.python.org/3/library/stdtypes.html#bytes.fromhex
    
- Tabla ASCII oficial  
    [https://www.asciitable.com](https://www.asciitable.com)
    
- Manual de Netcat (Linux Man Page)  
    [https://linux.die.net/man/1/nc](https://linux.die.net/man/1/nc)
    
- picoCTF Learning Resources  
    [https://play.picoctf.org/practice](https://play.picoctf.org/practice)