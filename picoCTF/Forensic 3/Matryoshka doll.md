## Matryoshka doll
## Descripcion
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one?Image: [dolls.jpg](https://challenge-files.picoctf.net/c_wily_courier/feaddb84eaaa2f8d6b83bda9e7a9c46a86474361e095fea9ee3840873f3506b4/dolls.jpg)

## solucion
- verificamos en tipo de archivo

`file dolls.jpg` 

- verificamos si tiene contenido anexo con `binwalk`, hay un archivo .zip dentro

`binwalk dolls.jpg`  

- extraemos el archivo .zip , se crea un diectorio `base_images` y dentro de el hay otra imagen

`unzip dolls.jpg`  

- repetimos el proceso de extracción hasta obtener la bandera

**picoCTF{LL9lb1dR4QbGe4l4iWCvGq9pdtwt7392}**
## Notas
### Esteganografía

Steganography

- Técnica para ocultar información dentro de otros archivos
    
- En este caso: archivos comprimidos dentro de imágenes

###  Archivos incrustados

- Un archivo puede contener otros archivos dentro de su estructura binaria
    
- No son visibles al abrir normalmente
### Extracción recursiva

- Proceso repetitivo para descubrir múltiples capas ocultas
    
- Muy común en retos CTF
## Referencias
- Binwalk Documentation
    
- Steganography Overview
    
- Manual de comandos Linux (`file`, `unzip`)
    
- Recursos de análisis forense digital



