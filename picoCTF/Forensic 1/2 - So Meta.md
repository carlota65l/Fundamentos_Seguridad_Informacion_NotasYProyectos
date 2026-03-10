## So Meta
## Descripcion

## Solucion


### solucion 1 kali
|   |   |
|---|---|
|**`wget --user-agent`**|Descargar archivos cuando el servidor te bloquea.|
|**`exiftool`**|Leer información oculta en los tags (campos) del archivo.|
|**`strings`**|Encontrar texto plano "embarrado" en el código binario.|
|**`binwalk`**|Detectar y extraer archivos ocultos dentro de otros.|

picoCTF{s0_m3ta_74af23ab}

## Notas

En retos de categoría **Forensics** o **Steganography** (esteganografía), los archivos suelen ser "contenedores" de secretos. Aquí tienes una guía de dónde buscar cuando una imagen parece normal:

#### A. Metadatos (Nivel Básico)

Como acabas de ver, los metadatos son el primer lugar donde mirar.

- **Comando clave:** `exiftool nombre_imagen.jpg` (sin parámetros para ver todo).
    
- **Campos sospechosos:** `Comment`, `Artist`, `Author`, `Description`, `Copyright`.
    

#### B. Cadenas de texto ocultas (Nivel Medio)

A veces la flag no está en un "campo" oficial, sino simplemente escrita al final del código binario del archivo.

- **Herramienta:** `strings`
    
- **Comando:** `strings nombre_imagen.png | grep "picoCTF"`
    
- _¿Qué hace?_ Busca cualquier secuencia de caracteres legibles dentro del archivo y filtra los que coincidan con el formato de la flag.
    

#### C. Archivos dentro de archivos (Nivel Avanzado)

Una imagen puede tener un archivo ZIP o un archivo de texto escondido dentro de ella.

- **Herramienta:** `binwalk`
    
- **Comando:** `binwalk -e nombre_imagen.png`
    
- _¿Qué hace?_ Analiza la estructura del archivo y extrae (`-e`) cualquier dato oculto que encuentre (como otras imágenes o archivos comprimidos).
    

#### D. Esteganografía con contraseña

Si nada de lo anterior funciona, la flag podría estar cifrada dentro de los píxeles.

- **Herramienta:** `steghide`
    
- **Comando:** `steghide extract -sf nombre_imagen.jpg`
    
- _Nota:_ Suele requerir una contraseña (passphrase).

## Referencias
