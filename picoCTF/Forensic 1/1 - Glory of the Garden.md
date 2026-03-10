## Glory of the Garden

## Descripcion
This file contains more than it seems.Get the flag from [garden.jpg](https://challenge-files.picoctf.net/c_fickle_tempest/26ad1e959e2e6f15113d4dc2b43649625499d960e546d1b874357c6fcb8c5229/garden.jpg).
## Solucion

### solucion 1 hex
Búsqueda de Strings (Cadenas de texto)

Dentro del editor hexadecimal (como GHex o Hexcurse), usa la función de búsqueda (**Ctrl+F**) para buscar el formato del flag:

- Busca la cadena: `picoCTF{`
    
- Si no aparece completa, busca solo `pico` o `CTF`.
    
- **Nota:** A veces el flag está al final del archivo, en los metadatos de "Comentarios".

**picoCTF{more_than_m33ts_the_3y333f84d7c}**

## Notas

#### Técnica de "Carving" (Binwalk)

Si notas que el archivo es muy pesado para ser solo una imagen (el tuyo pesa **2.2MB**, lo cual es sospechoso para un reto simple), es posible que haya otro archivo pegado dentro.

- **Comando:** `binwalk -e garden.jpg`
    
- Esto extraerá cualquier archivo oculto (como un `.zip` o un `.txt`) que esté embebido en los datos hexadecimales.
## Referencias
MétodoHerramientaCuándo usarlo**Hex Check**`ghex` / `xxd`Para ver si hay texto plano o archivos concatenados al final.**Strings**`strings`Para volcar todo el texto legible del binario rápidamente.**Metadata**`exiftool`Si sospechas que el flag está en los datos de la cámara o autor.**Steganography**`steghide`Si el flag está encriptado dentro de los píxeles (necesitarás password).