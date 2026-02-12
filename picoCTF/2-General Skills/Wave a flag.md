## Wave a flag
## Descripcion
Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...[warm](https://challenge-files.picoctf.net/c_wily_courier/70013ed41d4cfe2bb48628471dac6fc12238b5dbe164301ae3b4e35277b1e80b/warm)

## Solucion
### solucion 1_ usando python

Este es un reto de:

- Uso básico de terminal Linux
    
- Permisos de archivos
    
- Argumentos de línea de comandos


```bash
BelovedCis-picoctf@webshell:~$ cmod +xwarm -bash: cmod: command not found 
BelovedCis-picoctf@webshell:~$ ./warm -bash: ./warm: Permission denied 
BelovedCis-picoctf@webshell:~$ cmod +x warm -bash: cmod: command not found 
BelovedCis-picoctf@webshell:~$ chmod +x warm 
BelovedCis-picoctf@webshell:~$ ./warm Hello user! Pass me a -h to learn what I can do! 
BelovedCis-picoctf@webshell:~$ ./warm -h Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_ac5832c} 
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{learning_about_converting_values_aa2bA794}

## Notas
El `./` indica que el ejecutable está en el directorio actual.

Linux no ejecuta archivos del directorio actual automáticamente por seguridad.


## Referencias
- Python Documentation – Built-in Functions  
    https://docs.python.org/3/library/functions.html#chr
    
- Python Documentation – bytes.fromhex()  
    https://docs.python.org/3/library/stdtypes.html#bytes.fromhex
    
- Manual de Netcat (Linux Man Page)  
    [https://linux.die.net/man/1/nc](https://linux.die.net/man/1/nc)
    