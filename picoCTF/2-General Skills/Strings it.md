## Strings it
## Descripcion
Can you find the flag in [file](https://challenge-files.picoctf.net/c_fickle_tempest/fd00e7cc9b263f22c323572d2d5fc37d170f8e58e99a91f8991d0f07c69b21ff/strings) without running it?
## Solucion
### solucion 1_ usando python

- strings strings | grep picoCTF

 
```bash
BelovedCis-picoctf@webshell:~$ ls README.txt strings strings.1 
BelovedCis-picoctf@webshell:~$ ls -ls total 1544 8 -rw-r--r-- 1 root root 4443 Feb 11 18:30 README.txt 768 -rw-rw-r-- 1 
BelovedCis-picoctf BelovedCis-picoctf 784424 Nov 14 19:58 strings 768 -rw-rw-r-- 1 BelovedCis-picoctf BelovedCis-picoctf 784424 Nov 14 19:58 strings.1 
BelovedCis-picoctf@webshell:~$ ls -la strings -rw-rw-r-- 1 
BelovedCis-picoctf 
BelovedCis-picoctf 784424 Nov 14 19:58 strings
BelovedCis-picoctf@webshell:~$ file strings strings: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=9afb1d75e4657d085f4fa831028ee0fcad4437b7, for GNU/Linux 3.2.0, not stripped BelovedCis-picoctf@webshell:~$ chmod +x strings 
BelovedCis-picoctf@webshell:~$ ls -la strings -rwxrwxr-x 1 
BelovedCis-picoctf 
BelovedCis-picoctf 784424 Nov 14 19:58 strings 
BelovedCis-picoctf@webshell:~$ ./strings Maybe try the 'strings' function? Take a look at the man page 
BelovedCis-picoctf@webshell:~$ man strings \ > 
BelovedCis-picoctf@webshell:~$ strings strings | grep pico picoCTF{5tRIng5_1T_FB7D7Bb6} 
```

Respuesta:picoCTF{5tRIng5_1T_FB7D7Bb6}


## Notas

- - **ELF** → Executable and Linkable Format (ejecutable en Linux)
    
- **64-bit** → arquitectura x86-64
    
- **PIE** → Position Independent Executable
    
- **Dynamically linked** → usa librerías del sistema
    
- **Not stripped** → conserva símbolos (más fácil de analizar)

El ejecutable no ofuscó la flag.  
La flag estaba almacenada como texto ASCII dentro del binario, por lo que `strings` pudo extraerla fácilmente.

### Herramientas utilizadas

- `ls`
    
- `file`
    
- `chmod`
    
- `strings`
    
- `grep`

## Referencias
- **Este reto demuestra la importancia del análisis estático en ingeniería inversa. A través del uso del comando `strings`, fue posible identificar texto embebido en un ejecutable ELF sin necesidad de ejecutarlo. Esto resalta cómo información sensible puede quedar expuesta en binarios si no se aplican técnicas de ofuscación o protección adecuadas.**