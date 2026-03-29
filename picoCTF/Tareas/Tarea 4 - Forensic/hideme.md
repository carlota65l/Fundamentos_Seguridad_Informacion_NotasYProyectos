## hideme
## Descripcion

Every file gets a flag.The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/259/flag.png).
## Solucion
usar `binwalk` con la bandera `-e` (extract) para automatizar este proceso:

Bash

```
binwalk -e flag.png
```

**picoCTF{Hiddinng_An_imag3_within_@n_ima9e_cda72af0}**
## Notas

- **Archivos Anidados (Nested Files):** Es una técnica básica de ocultamiento donde un archivo (a menudo un archivo comprimido como `.zip` o `.tar`) se adjunta al final del código binario de un archivo contenedor (como una imagen `.png` o `.jpg`).
    
- **Firmas de Archivos (Magic Bytes / File Signatures):** Los sistemas operativos y las herramientas forenses no confían en la extensión del archivo (por ejemplo, `.png`), sino en los "Magic Bytes", que son los primeros bytes de un archivo y definen su verdadero formato.
    
- **Marcadores de Fin de Archivo (EOF - End of File):** Un visor de imágenes normal lee los datos de la imagen desde los Magic Bytes iniciales hasta encontrar el marcador que indica el "final de la imagen". Todo el código binario que se pegue _después_ de ese marcador es ignorado por el visor de imágenes (por eso la imagen se ve normal), pero sigue presente en el archivo y puede ser extraído.

## Referencias

- **Sobre el uso y funcionamiento de Binwalk:** ReFirm Labs. (s.f.). _Binwalk - Firmware Analysis Tool_. Repositorio oficial en GitHub. Recuperado de: [https://github.com/ReFirmLabs/binwalk](https://github.com/ReFirmLabs/binwalk)

- **Sobre las Firmas de Archivos (Magic Bytes):** Kessler, G. C. (s.f.). _File Signatures Table_. Recuperado de: [https://www.garykessler.net/library/file_sigs.html](https://www.garykessler.net/library/file_sigs.html) _(Nota: Esta es una de las referencias más citadas en análisis forense para identificar tipos de archivos)._

- **Sobre técnicas de ocultamiento (Archivos Anidados):** EC-Council. (s.f.). _Computer Forensics Investigating Data and Image Files_. En _Computer Hacking Forensic Investigator (CHFI)_.