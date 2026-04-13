## interencdec
## Descripcion

Can you get the real meaning from this file.Download the file [here](https://artifacts.picoctf.net/c_titan/109/enc_flag).
## Solucion
Paso 1: Primera decodificación Base64: `cat enc_flag | base64 -d`

 Paso 2: Segunda decodificación Base64: Tomar la cadena resultante y decodificarla de nuevo: `echo "[cadena]" | base64 -d`
 Paso 3: Descifrado César (ROT-7): Aplicar una rotación de -7 (o 19) para convertir el texto `wpjvJAM...` a `picoCTF...`.

**picoCTF{caesar_d3cr9pt3d_f0212758} **
## Notas
**Codificación (Encoding) vs. Cifrado (Encryption):** * **Codificación:** Transforma datos a un formato estandarizado para que puedan ser leídos o transmitidos fácilmente por distintos sistemas. **No proporciona seguridad**. Cualquier persona que sepa qué método se usó (como Base64) puede revertirlo fácilmente.

- **Cifrado:** Oculta la información usando un algoritmo y, usualmente, una "llave" secreta. Su objetivo es que solo quienes posean la llave o descubran la lógica oculta puedan leer el mensaje (como el Cifrado César).
## Referencias
https://gchq.github.io/CyberChef/#recipe=ROT13(true,true,false,19)&input=d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fSA