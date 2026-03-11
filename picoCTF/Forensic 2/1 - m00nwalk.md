## m00nwalk
## Descripcion
Decode this [message](https://challenge-files.picoctf.net/c_fickle_tempest/5593bde2464fd1977048cba02daa086d1fbc0fada1ef8521169ccdad2f19c6fc/message.wav) from the moon.
## Solucion
### solucion 1_ decodificando senial

-Verificamos el tipo de archivo con file

`file message.wav` 

- Descargamos decodificador STTV de github y lo instalamos
 [https://github.com/colaclanth/sstv](https://github.com/colaclanth/sstv "https://github.com/colaclanth/sstv")

`cd /opt sudo git clone https://github.com/colaclanth/sstv cd sstv https://github.com/colaclanth/sstv`

- Decodificamos el mensaje oculto en el .wav y lo guardamos en flag.png

`sstv -d message.wav -o flag.png`

- Abrimos el archivo y copiamos la flag

`open flag.png`

picoCTF{beep_boop_im_in_space}
## Notas
### ¿Qué es SSTV (Televisión de Barrido Lento)?

Originalmente, el SSTV fue diseñado por radioaficionados para transmitir imágenes fijas (fotografías) a través de ondas de radio de banda estrecha (como las de voz).

- **Cómo funciona:** La imagen se convierte en una serie de tonos de audio. Cada frecuencia de sonido representa un color o brillo diferente, y el tiempo determina la posición del píxel.
    
- **El sonido característico:** Si escuchas el archivo `message.wav`, oirás una serie de chirridos rítmicos y ruidos estáticos que parecen de ciencia ficción o de un módem antiguo.
## Referencias
- **`file message.wav`**: Es el primer paso vital. Te confirma que es un archivo de audio real y no un archivo de texto con extensión falsa. Los retos de SSTV suelen usar formato `.wav` porque es un formato "sin pérdida" (lossless), lo que evita que la compresión (como la de un MP3) destruya los datos de la imagen.
    
- **Instalación del decodificador**: El repositorio de `colaclanth` es una implementación en Python que "escucha" el audio y reconstruye la matriz de píxeles basándose en las variaciones de frecuencia.
    
- **`sstv -d message.wav -o flag.png`**:
    
    - `-d`: Indica el archivo de entrada (decode).
        
    - `-o`: Indica el nombre del archivo de salida.
        
    - **Detección automática de modo:** Existen varios "modos" de SSTV (Martin M1, Scottie S1, Robot 36). La herramienta intenta detectar automáticamente cuál se usó analizando la cabecera del audio.