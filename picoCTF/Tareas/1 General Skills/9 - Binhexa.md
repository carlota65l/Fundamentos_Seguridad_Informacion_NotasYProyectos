## Binhexa
## Descripcion

How well can you perfom basic binary operations?Start searching for the flag here `nc titan.picoctf.net 65227`
## Solucion
### solucion 1_ usando python



 
```bash
BelovedCis-picoctf@webshell:~$ nc titan.picoctf.net 65227

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 10110110
Binary Number 2: 00001010


Question 1/6:
Operation 1: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11000000
Correct!

Question 2/6:
Operation 2: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11100011100
Correct!

Question 3/6:
Operation 3: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 101101100
Correct!

Question 4/6:
Operation 4: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 00000010
Correct!

Question 5/6:
Operation 5: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10111110
Correct!

Question 6/6:
Operation 6: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 00000101
Correct!

Enter the results of the last operation in hexadecimal: 0x5

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_1367e2c6}

```

Respuesta: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_1367e2c6}


## Notas

**Sistema binario** es la base numérica 2, donde solo existen los dígitos `0` y `1`. Es la base de toda la computación moderna.

**Conversión entre bases:**

- Binario → Decimal: multiplicar cada bit por su potencia de 2
- Decimal → Hexadecimal: dividir entre 16 y tomar residuos
- Binario → Hexadecimal: agrupar de 4 en 4 bits

**Operaciones bitwise** operan directamente sobre los bits individuales de un número y son fundamentales en criptografía, compresión, redes y sistemas embebidos.

|Operación|Símbolo|Descripción|
|---|---|---|
|AND|`&`|1 solo si ambos bits son 1|
|OR|`\|`|1 si al menos un bit es 1|
|XOR|`^`|1 si los bits son diferentes|
|NOT|`~`|Invierte todos los bits|
|Left Shift|`<<`|Desplaza bits a la izquierda (× 2^n)|
|Right Shift|`>>`|Desplaza bits a la derecha (÷ 2^n)|

**Netcat (`nc`)** es una herramienta de red que permite conectarse a puertos TCP/UDP desde la terminal, muy usada en CTFs para interactuar con servicios remotos.
## Referencias
- Khan Academy — Sistemas numéricos: [https://www.khanacademy.org/math/cc-eighth-grade-math/cc-8th-numbers-operations/cc-8th-scientific-notation-compu/a/bits-and-binary](https://www.khanacademy.org/math/cc-eighth-grade-math/cc-8th-numbers-operations/cc-8th-scientific-notation-compu/a/bits-and-binary)
- Tutorials Point — Binary Arithmetic: [https://www.tutorialspoint.com/computer_logical_organization/binary_arithmetic.htm](https://www.tutorialspoint.com/computer_logical_organization/binary_arithmetic.htm)

**Operaciones bitwise:**

- MDN Web Docs — Bitwise operators: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_operators#bitwise_operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_operators#bitwise_operators)
- GeeksforGeeks — Bitwise operators: [https://www.geeksforgeeks.org/bitwise-operators-in-c-cpp/](https://www.geeksforgeeks.org/bitwise-operators-in-c-cpp/)

**Conversión de bases:**

- RapidTables — Conversores online: [https://www.rapidtables.com/convert/number/](https://www.rapidtables.com/convert/number/)