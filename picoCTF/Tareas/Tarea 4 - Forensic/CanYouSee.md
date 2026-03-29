## CanYouSee
## Descripcion

How about some hide and seek?Download this file [here](https://artifacts.picoctf.net/c_titan/129/unknown.zip).
## Solucion
Al descargar y descomprimir el archivo `unknown.zip`, encontramos una imagen llamada `ukn_reality.jpg`. Puesto que se trataba de un reto de esteganografía o análisis forense básico, el comando de búsqueda de texto simple (`grep`) no funcionó de inmediato porque la _flag_ estaba oculta dentro de la estructura de la imagen. La solución consistió en utilizar herramientas de línea de comandos en Kali Linux diseñadas para analizar el interior de archivos binarios, tales como `strings` (para buscar texto legible), `exiftool` (para revisar metadatos ocultos) o `binwalk` (para buscar y extraer archivos incrustados dentro de la imagen).

**picoCTF{ME74D47A_HIDD3N_b32040b8}**


## Notas
strings`: Extrae cadenas de texto de archivos binarios.
 `exiftool`: Lee y escribe metadatos en archivos.

`binwalk`: Busca y extrae firmas de archivos incrustados en otros archivos.

## Referencias

CyberChef: La "Navaja Suiza" web para cifrado, decodificación, compresión y análisis de datos. Muy útil en CTFs. ([https://gchq.github.io/CyberChef/](https://gchq.github.io/CyberChef/))