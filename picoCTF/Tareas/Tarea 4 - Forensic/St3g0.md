## St3g0
## Descripcion
Download this image and find the flag.

- [Download image](https://artifacts.picoctf.net/c/216/pico.flag.png)

## Solucion


**picoCTF{7h3r3_15_n0_5p00n_a1062667}**

## Notas

- **Esteganografía:** A diferencia de la criptografía (que oculta el _significado_ de un mensaje), la esteganografía es la práctica de ocultar la _existencia_ misma del mensaje. Se logra camuflando información secreta dentro de archivos digitales comunes, como imágenes, audio o video.
    
- **Técnica LSB (Least Significant Bit / Bit Menos Significativo):** Es una de las técnicas esteganográficas más comunes. En una imagen digital, cada píxel tiene un color representado por valores binarios (bits) para los canales Rojo, Verde y Azul (RGB). Alterar el último bit (el menos significativo) de estos valores cambia el color del píxel de una forma tan minúscula que es imperceptible para el ojo humano, permitiendo esconder código binario (y por ende, texto) dentro de la imagen.
    
- **Importancia del formato PNG:** El formato `.png` utiliza compresión _sin pérdida_ (lossless), lo que significa que los datos exactos de los píxeles se conservan intactos. Esto es crucial para la técnica LSB, ya que si se usara un formato con pérdida como `.jpg`, la compresión destruiría los bits modificados y el mensaje oculto se perdería.
## Referencias

- **Sobre la Técnica LSB en Esteganografía:** Johnson, N. F., & Jajodia, S. (1998). _Exploring steganography: Seeing the unseen_. IEEE Computer, 31(2), 26-34. Recuperado de: [https://ieeexplore.ieee.org/document/64616](https://www.google.com/search?q=https://ieeexplore.ieee.org/document/64616) _(Nota: Este es un artículo clásico y muy citado académicamente sobre el tema)._
    
- **Sobre la herramienta zsteg:** Kolychev, A. [zed-0xff]. (s.f.). _zsteg: detect stegano-hidden data in PNG & BMP_. Repositorio de GitHub. Recuperado de: [https://github.com/zed-0xff/zsteg](https://github.com/zed-0xff/zsteg)
    
- **Sobre la diferencia entre compresión de imágenes y esteganografía:** W3C (World Wide Web Consortium). (s.f.). _Portable Network Graphics (PNG) Specification_. Recuperado de: [https://www.w3.org/TR/png/](https://www.w3.org/TR/png/)