## Static ain't always noise
## Descripcion
Can you look at the data in this binary? The bash script might help![static](https://challenge-files.picoctf.net/c_wily_courier/a7a487d82414dabf57a3ec5db604ae18c17b11406225839247539d5edb709957/static), [ltdis.sh](https://challenge-files.picoctf.net/c_wily_courier/a7a487d82414dabf57a3ec5db604ae18c17b11406225839247539d5edb709957/ltdis.sh)

**el uso de herramientas de ingeniería inversa para analizar ejecutables ELF sin necesidad de ejecutarlos directamente. Mediante el desensamblado y extracción de cadenas, fue posible identificar información sensible incrustada en el binario. Este tipo de análisis es fundamental en ciberseguridad para auditoría de software y análisis forense.**

## Solucion
### solucion 1_ usando python


- Identificar la base numérica.
    
- Convertir a decimal.
    
- Convertir decimal a ASCII.
    
- Unir los caracteres.
    
- Responder exactamente como pide el servidor.
 
```bash
BelovedCis-picoctf@webshell:~$ wget https://challenge-files.picoctf.net/c_wily_courier/a7a487d82414dabf57a3ec5db604ae18c17b11406225839247539d5edb709957/static --2026-02-11 18:41:20-- https://challenge-files.picoctf.net/c_wily_courier/a7a487d82414dabf57a3ec5db604ae18c17b11406225839247539d5edb709957/static Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 3.160.5.18, 3.160.5.64, 3.160.5.40, ... 
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|3.160.5.18|:443... connected. HTTP request sent, awaiting response... 200 OK Length: 16776 (16K) [application/octet-stream] Saving to: 'static' static 100%[==================>] 16.38K --.-KB/s in 0.006s 2026-02-11 18:41:20 (2.52 MB/s) - 'static' saved [16776/16776] 
BelovedCis-picoctf@webshell:~$ wget https://challenge-files.picoctf.net/c_wily_courier/a7a487d82414dabf57a3ec5db604ae18c17b11406225839247539d5edb709957/ltdis.sh --2026-02-11 18:41:39-- https://challenge-files.picoctf.net/c_wily_courier/a7a487d82414dabf57a3ec5db604ae18c17b11406225839247539d5edb709957/ltdis.sh Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 3.160.5.18, 3.160.5.40, 3.160.5.95, ... Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|3.160.5.18|:443... connected. HTTP request sent, awaiting response... 200 OK Length: 785 [application/octet-stream] Saving to: 'ltdis.sh' ltdis.sh 100%[==================>] 785 --.-KB/s in 0s 2026-02-11 18:41:39 (198 MB/s) - 'ltdis.sh' saved [785/785] 
BelovedCis-picoctf@webshell:~$ ls README.txt ltdis.sh static strings strings.1 warm 
BelovedCis-picoctf@webshell:~$ file static static: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=9a00d4dca6b92d22aa0cd1fceffa4ed7495b8534, for GNU/Linux 3.2.0, not stripped 
BelovedCis-picoctf@webshell:~$ file ltdis.sh ltdis.sh: Bourne-Again shell script, ASCII text executable 
BelovedCis-picoctf@webshell:~$ chmod +x ltdis.sh 
BelovedCis-picoctf@webshell:~$ ./ltdis.sh Attempting disassembly of ... objdump: 'a.out': No such file objdump: section '.text' mentioned in a -j option, but not found in any input file Disassembly failed! Usage: ltdis.sh <program-file> Bye! 
BelovedCis-picoctf@webshell:~$ ./ltdis.sh static Attempting disassembly of static ... Disassembly successful! Available at: static.ltdis.x86_64.txt Ripping strings from binary with file offsets... Any strings found in static have been written to static.ltdis.strings.txt with file offset 
BelovedCis-picoctf@webshell:~$ ls README.txt static static.ltdis.x86_64.txt strings.1 ltdis.sh static.ltdis.strings.txt strings warm 
BelovedCis-picoctf@webshell:~$ cat static.ltdis.strings.txt | grep pico 3020 picoCTF{d15a5m_t34s3r_20335e41}
```

Respuesta: picoCTF{d15a5m_t34s3r_20335e41}

## Notas
### Qué es `wget`?

Es una herramienta para descargar archivos desde internet mediante HTTP/HTTPS.
se descargo:

- `static` → binario ELF
    
- `ltdis.sh` → script de shell

### Desensamblado (Disassembly)
Proceso de convertir código máquina a lenguaje ensamblador.
Herramienta común:

`objdump -d archivo`

### Script de automatización
## Referencias
- Python Documentation – Built-in Functions  
    https://docs.python.org/3/library/functions.html#chr
    
- Python Documentation – bytes.fromhex()  
    https://docs.python.org/3/library/stdtypes.html#bytes.fromhex
    
- Manual de Netcat (Linux Man Page)  
    [https://linux.die.net/man/1/nc](https://linux.die.net/man/1/nc)
    