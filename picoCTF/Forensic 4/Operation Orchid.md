## Operation Orchid
## Descripcion
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/212/disk.flag.img.gz)
## Solucion
- Descomprimimos al archivo del reto, es nuevamente una imagen de disco a examinar
- Listamos las particiones:

`mmls disk.flag.img`

- Listamos los archivos en la partición Linux donde estan los datos

`fls -o 411648 disk.flag.img`

- Vemos el archivo con el historial de comandos, para ver como fue encriptada la bandera

`icat -i raw -o 411648 disk.flag.img 1875`

- Vemo el archivo que tiene la bandera encriptada:

`icat -o 411648  disk.flag.img 1782`

- Grabamos la bandera encriptada en un archivo local:

`icat -o 411648  disk.flag.img 1782 > flag.txt.enc`

- Desencriptamos la bandera, haciendo las operaciones inversas que se usaron para encriptarla

`openssl aes256 -salt -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567`

- Mostrmos la bandera:

`cat flag.txt`

**picoCTF{h4un71ng_p457_0a710765}**
## Notas
#### Inodos

- Identificadores internos de archivos en sistemas Linux.
- Permiten recuperar archivos sin depender del nombre.
#### Herramientas utilizadas

- The Sleuth Kit  
    Análisis de imágenes de disco.
- mmls  
    Identificación de particiones.
- fls  
    Listado de archivos.
- icat  
    Extracción de archivos.
- OpenSSL  
    Descifrado de archivos.
## Referencias
- OpenSSL  
    [https://www.openssl.org/](https://www.openssl.org/)
- The Sleuth Kit  
    [https://www.sleuthkit.org/](https://www.sleuthkit.org/)
- Cifrado AES  
    Estándar de cifrado simétrico.
- picoCTF  
    [https://picoctf.org/](https://picoctf.org/)