## c0rrupt
## Descripcion
We found this [file](https://challenge-files.picoctf.net/c_fickle_tempest/87bdc8ce30b177d033b3d68bca4647950bb07304032861baa912ebe08701d355/mystery). Recover the flag.
## Solucion
Al revisar el contenido hexadecimal del archivo, identifiqué tres errores críticos en la estructura (los "Magic Bytes") que impiden que se abra como una imagen:

1. **Firma PNG corrupta (Bytes 0-3):**
    
    - **Lo que tiene tu archivo:** `89 65 4E 34` (En texto se lee como `‰eN4`).
        
    - **Lo que debería tener:** `89 50 4E 47` (La firma estándar de un PNG es `.PNG`).
        
2. **Segunda parte de la firma (Bytes 4-7):**
    
    - **Lo que tiene tu archivo:** `0D 0A B0 AA`.
        
    - **Lo que debería tener:** `0D 0A 1A 0A` (Estos bytes controlan cómo los sistemas manejan los saltos de línea).
        
3. **Nombre del primer bloque (Chunk IHDR):**
    
    - **Lo que tiene tu archivo:** En la posición `0000000C` dice `43 22 44 52` (que se lee como `C"DR`).
        
    - **Lo que debería tener:** `49 48 44 52` (El bloque de cabecera siempre debe llamarse `IHDR`).
### solucion 1_

Para recuperar la imagen y ver la "Flag" del reto, sigue estos pasos:

1. Abre un editor hexadecimal (como **Hexed.it** en tu navegador).
    
2. Sube el archivo `mystery`.
    
3. **Cambia los primeros 8 bytes:**
    
    - Haz clic en el primer byte (`89`) y asegúrate de que los primeros 8 valores sean exactamente: `89 50 4E 47 0D 0A 1A 0A`
        
4. **Corrige el nombre del bloque IHDR:**
    
    - Busca la cadena `C"DR` (o ve a la posición `0C`) y sobrescribe esos 4 bytes para que digan: `49 48 44 52`
        
5. **Guarda el archivo:**
    
    - Exporta el archivo con el nombre `reparado.png`.

**picoCTF{c0rrupt10n_1847995}**
## Notas

Un archivo PNG no es solo una imagen; es una secuencia de bloques llamados **chunks**. Para que un programa lo abra, los bloques críticos deben ser perfectos:

- **Firma del Archivo (Magic Bytes):** Todo PNG debe comenzar exactamente con estos 8 bytes (en hexadecimal): `89 50 4E 47 0D 0A 1A 0A`.
    
    - _Nota del ejercicio:_ En tu archivo `mystery`, estos estaban cambiados por `89 65 4E 34 0D 0A B0 AA`.
        
- **Chunk IHDR (Cabecera de imagen):** Es el primer bloque después de la firma. Contiene el ancho, alto y profundidad de color. Su nombre debe ser siempre `IHDR` (`49 48 44 52` en hex).
    
    - _Nota del ejercicio:_ El archivo tenía `C"DR` (`43 22 44 52`), lo cual es un error común en retos de CTF.
## Referencias

- **Hexed.it:** Editor hexadecimal online muy intuitivo para sobrescribir bytes manualmente.
    
- **`pngcheck`:** (Línea de comandos) Es la herramienta más importante. Al ejecutar `pngcheck mystery`, te dirá exactamente: _"Error: CRC error in chunk IHDR"_ o _"MNG error: Corrupt file signature"_.
    
- **`exiftool`:** Útil para ver metadatos ocultos que a veces contienen pistas sobre la "Flag".