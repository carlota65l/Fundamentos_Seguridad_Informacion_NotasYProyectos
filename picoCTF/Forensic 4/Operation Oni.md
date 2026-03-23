## Operation Oni
## Descripcion
Download this disk image, find the key and log into the remote machine. Note: if you are using the webshell, download and extract the disk image into /tmp not your home directory. Download disk image Remote machine: ssh -i key_file -p 56275 ctf-player@saturn.picoctf.net
## Solucion
- Descomprimimos el archivo y vemos que se trata de otra imagen de disco para examinar
- Mostramos las particiones:

`mmls disk.img` 

- Listamos archivos en la particion de datos:

`fls -o 206848 disk.img`

- Listamos archivos de la carpetar root, luego carpeta .ssh, buscando la llave privada para acceder por ssh

`fls -o 206848 disk.img 470 fls -o 206848 disk.img 3916`

- Descargamos la llave privada a un archivo local:

`icat -o 206848 disk.img 2345 > id_rsa`

- Cambiamos los permisos de la llave y nos conetamos por ssh:

`chmod 600 id_rsa ssh -i id_rsa -p 64715 ctf-player@saturn.picoctf.net`

- Listamos archivos y mostramos la bandera

`ls cat flag.txt`

**picoCTF{k3y_5l3u7h_af277f77}**
## Notas
Este ejercicio de picoCTF combina:

- Análisis forense digital
- Uso de credenciales encontradas
- Acceso remoto con SSH

👉 La idea es:

> Encontrar una clave privada en disco y reutilizarla para acceso.
## Referencias
 OpenSSL  
    [https://www.openssl.org/](https://www.openssl.org/)
- The Sleuth Kit  
    [https://www.sleuthkit.org/](https://www.sleuthkit.org/)
- Cifrado AES  
    Estándar de cifrado simétrico.
- picoCTF  
    [https://picoctf.org/](https://picoctf.org/)