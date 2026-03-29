## RED
## Descripcion

RED, RED, RED, REDDownload the image: [red.png](https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png)
## Solucion
LSB es una técnica clásica de esteganografía donde se esconde información en los últimos bits de los píxeles de una imagen.

Sabiendo esto, puedes usar la herramienta `zsteg` (la misma que usamos en el reto _St3g0_) para escanear y extraer el contenido oculto en los canales de color (RGBA):

Bash

```
zsteg red.png
```

El resultado de este comando revelará una cadena de texto sospechosa que se repite: `cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==`

**picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_} **
## Notas

- **Acrósticos en Metadatos:** El uso de metadatos (como comentarios o descripciones dentro de un archivo de imagen) no siempre alberga la respuesta final. En técnicas forenses, a menudo contienen pistas secundarias. En este caso, un poema funcionó como un acróstico, donde la primera letra de cada línea formaba una instrucción oculta (`CHECKLSB`).

- **Esteganografía LSB (Least Significant Bit) en RGBA:** A diferencia de una imagen RGB estándar, las imágenes PNG pueden tener un canal "Alpha" (RGBA), que controla la opacidad/transparencia. La técnica LSB puede esconder datos alterando el último bit de cualquiera de estos canales de color sin que el ojo humano note la diferencia.

- **Ofuscación en Capas (Doble Ocultamiento):** Este ejercicio demuestra una técnica de defensa/ocultamiento en profundidad. El atacante (o creador del reto) no solo escondió el texto dentro de los píxeles de la imagen mediante LSB, sino que el texto resultante estaba codificado en **Base64** (`cGlj...==`), requiriendo un paso adicional de decodificación para obtener el texto plano.
## Referencias

 **Sobre el análisis de Metadatos con ExifTool:** Harvey, P. (s.f.). _ExifTool Documentation_. Recuperado de: [https://exiftool.org/](https://exiftool.org/)

-**Sobre la codificación Base64 (estándares de ofuscación):** Josefsson, S. (2006). _The Base16, Base32, and Base64 Data Encodings (RFC 4648)_. Internet Engineering Task Force (IETF). Recuperado de: [https://datatracker.ietf.org/doc/html/rfc4648](https://datatracker.ietf.org/doc/html/rfc4648)

**Herramienta alternativa para decodificar (Opcional para mencionar):** GCHQ. (s.f.). _CyberChef: The Cyber Swiss Army Knife_. Recuperado de: [https://gchq.github.io/CyberChef/](https://gchq.github.io/CyberChef/)