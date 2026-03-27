## HashingJobApp

## Descripcion
If you want to hash with the best, beat this test!

nc saturn.picoctf.net 49248
## Solucion

**picoCTF{4ppl1c4710n_r3c31v3d_674c1de2}**
## Notas
#### Hash MD5

- MD5 es una **función hash criptográfica** que transforma cualquier entrada en una cadena hexadecimal de longitud fija.
- Es una función **unidireccional** (no se puede revertir fácilmente).
- Se usa para verificación de integridad (aunque ya no es segura para criptografía moderna).

👉 En este reto:

- No se rompe el hash
- Solo se **calcula directamente**
## Referencias

- Tan, J. W. (2024). _HashingJobApp Writeup_.  
    Explica que el reto pide generar hashes MD5 múltiples veces para obtener la flag.
- Wei, P. (2022). _PicoCTF HashingJobApp_.  
    Describe el uso de Python (`hashlib`) para automatizar el cálculo de hashes.
- Ahmed Heltaher (2025). _CTF Writeup_.  
    Muestra ejemplos usando `md5sum` y cómo repetir el proceso hasta obtener la flag.
- Brooks, L. (2022). _Medium Writeup_.  
    Explica el uso de Netcat y herramientas externas para generar hashes MD5.
- Hedeenza (2024). _Arboreal Repository_.  
    Señala el error común del salto de línea y la importancia de `echo -n`.