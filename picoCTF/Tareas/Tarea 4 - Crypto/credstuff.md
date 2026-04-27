## credstuff
## Descripcion
We found a leak of a blackmarket website's login credentials. Can you find the password of the user `cultiris` and successfully decrypt it?Download the leak [here](https://artifacts.picoctf.net/c/151/leak.tar).The first user in `usernames.txt` corresponds to the first password in `passwords.txt`. The second user corresponds to the second password, and so on.
## Solucion

- **Extraer los archivos:** Al descargar y descomprimir el archivo `leak.tar`, obtendrás una carpeta con dos archivos de texto: `usernames.txt` y `passwords.txt`.
    
- **Buscar al usuario:** Necesitamos encontrar en qué número de línea se encuentra el usuario `cultiris` dentro del archivo `usernames.txt`. Si usas un comando en la terminal como `grep -n cultiris usernames.txt` (o simplemente la función de búsqueda "Ctrl+F" en tu editor de texto), descubrirás que `cultiris` se encuentra exactamente en la **línea 378**.
    
- **Encontrar la contraseña:** Sabiendo que cada usuario coincide con su contraseña línea por línea, debes buscar la **línea 378** del archivo `passwords.txt`. Al revisarla, encontrarás este texto cifrado: `cvpbPGS{P7e1S_54I35_71Z3}`
    
- **Descifrar la contraseña:** El texto claramente conserva el formato de las flags de la competencia (`picoCTF{...}`), pero las letras están alteradas. Esto es un indicio de que se utilizó el cifrado de sustitución **ROT13** (que rota cada letra 13 posiciones en el alfabeto). Los números y caracteres especiales no cambian.

cvpbPGS{P7e1S_54I35_71Z3}

**picoCTF{C7r1F_54V35_71M3}**
## Notas
Al aplicar ROT13 al texto cifrado obtenemos:

- `cvpbPGS` se convierte en `picoCTF`
    
- `P7e1S_54I35_71Z3` se convierte en `C7r1F_54V35_71M3`
## Referencias
https://gchq.github.io/CyberChef/#recipe=ROT13(true,true,false,13)&input=Y3ZwYlBHU3tQN2UxU181NEkzNV83MVozfQ