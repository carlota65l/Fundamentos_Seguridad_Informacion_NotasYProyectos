## rail-fence
## Descripcion
A type of transposition cipher is the rail fence cipher, which is described [here](https://en.wikipedia.org/wiki/Rail_fence_cipher). Here is one such cipher encrypted using the rail fence with 4 rails. Can you decrypt it?Download the message [here](https://artifacts.picoctf.net/c/188/message.txt).Put the decoded message in the picoCTF flag format, `picoCTF{decoded_message}`.
## Solucion


El mensaje encriptado tiene exactamente 56 caracteres. Cuando utilizamos el Rail Fence Cipher con 4 niveles (rieles), las letras se distribuyen matemáticamente basándose en un ciclo continuo que sube y baja. Al separar la cadena de texto original en sus respectivos rieles obtenemos las siguientes secuencias:

- **Riel 1 (10 caracteres):** `Ta _7N6D49`
    
- **Riel 2 (19 caracteres):** `hlg:W3D_H3C31N__A97`
    
- **Riel 3 (18 caracteres):** `ef sHR053F38N43D7B`
    
- **Riel 4 (9 caracteres):** `i33___N6`
    

Al reconstruir el mensaje leyendo de arriba hacia abajo y de izquierda a derecha siguiendo el camino en zigzag, los fragmentos se unen formando el mensaje descifrado a la perfección.

**picoCTF{WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_4A76B997}**
## Notas
In the rail fence cipher, the plaintext is written downwards diagonally on successive "rails" of an imaginary fence, then moving up when the bottom rail is reached, down again when the top rail is reached, and so on until the whole plaintext is written out. The ciphertext is then read off in rows.

For example, to encrypt the message 'WE ARE DISCOVERED. RUN AT ONCE.' with 3 "rails", write the text as:

W . . . E . . . C . . . R . . . U . . . O . . . 
. E . R . D . S . O . E . E . R . N . T . N . E 
. . A . . . I . . . V . . . D . . . A . . . C .

(Spaces and punctuation are omitted.) Then read off the text horizontally to get the ciphertext:

WECRUO ERDSOEERNTNE AIVDAC
## Referencias
https://en.wikipedia.org/wiki/Rail_fence_cipher