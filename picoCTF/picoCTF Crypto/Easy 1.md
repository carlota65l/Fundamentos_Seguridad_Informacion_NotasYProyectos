##  Easy 1
## Descripcion

The one time pad can be cryptographically secure, but not when you know the key. Can you solve this?We've given you the encrypted flag, key, and a table to help UFJKXQZQUNB with the key of SOLVECRYPTO. Can you use this [table](https://challenge-files.picoctf.net/c_fickle_tempest/859ffc313a4d8b63149f144745043a7312fc4f993e405eeeb8ee5ae6ca8444a8/table.txt) to solve it?.
## Solucion

### Forma 1 - Manual usando la tabla
- Descargar la tabla de viegenere que nos dan en el reto
- Toma una letra de la bandera encriptada y una letra de la llave
Una letra del texto cifrado: U
Una letra de la llave: S
- Se busca la S en la columna vertical
- Se avanza horizontalmente hasta la U
- Donde se cruzan subes hasta la cabecera tomas C
### Forma 2 - Cyberchef
- Ir a cyberchef
- Usar la recera: viegenere
### Forma 3 - Python IA
- Pedir a lA: Crear un script en python para decodificar una cadena con el algoritmo de viegenere dada una llave
**picoCTF{CRYPTOISFUN}**
## Notas
- El reto simula un **One-Time Pad**, pero:
    - La clave es conocida → deja de ser seguro
- En realidad es un **Vigenère cipher**, que:
    - Usa una clave repetida
    - Es vulnerable si conoces la clave
- La tabla proporcionada es solo una representación visual del algoritmo
## Referencias
https://es.wikipedia.org/wiki/Wikipedia:OneTimePad