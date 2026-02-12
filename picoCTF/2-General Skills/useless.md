## useless
## Descripcion
There's an interesting script in the user's home directory

Additional details will be available after launching your challenge instance.

**Connect with nc fickle-tempest.picoctf.net 56633.**

## Solucion
### solucion 1_ usando python


- Identificar la base numérica.
    
- Convertir a decimal.
    
- Convertir decimal a ASCII.
    
- Unir los caracteres.
    
- Responder exactamente como pide el servidor.
 
```bash
BelovedCis-picoctf@webshell:~$ ssh picoplayer@saturn.picoctf.net -p 55491
picoplayer@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 6.8.0-1044-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
Last login: Thu Feb 12 00:20:33 2026 from 3.140.102.47
picoplayer@challenge:~$ ls
useless
picoplayer@challenge:~$ cat useless
#!/bin/bash
# Basic mathematical operations via command-line arguments

if [ $# != 3 ]
then
  echo "Read the code first"
else
        if [[ "$1" == "add" ]]
        then 
          sum=$(( $2 + $3 ))
          echo "The Sum is: $sum"  

        elif [[ "$1" == "sub" ]]
        then 
          sub=$(( $2 - $3 ))
          echo "The Substract is: $sub" 

        elif [[ "$1" == "div" ]]
        then 
          div=$(( $2 / $3 ))
          echo "The quotient is: $div" 

        elif [[ "$1" == "mul" ]]
        then
          mul=$(( $2 * $3 ))
          echo "The product is: $mul" 

        else
          echo "Read the manual"
         
        fi
fi
picoplayer@challenge:~$ man -w useless | xargs zcat

.Dd 24/7/22               \" DATE
.Dt useless 1      \" Program name and manual section number
.Sh useless                 \" Section Header - required - don't modify
.Nm useless,
.Nd This is a simple calculator script
.Sh SYNOPSIS             \" Section Header - required - don't modify
.Nm
.Op add sub mul div              \" [-abcd]
.Ar number1  
.Ar number2  
              
.Sh DESCRIPTION          \" Section Header - required - don't modify
Use the 
.Nm 
macro to make simple calulations like addition,subtraction, multiplication and division.

.Sh Examples               
.Bl -tag -width 
.It Pa ./useless add 1 2
This will add 1 and 2 and return 3

.It Pa ./useless mul 2 3
This will return 6 as a product of 2 and 3

.It Pa ./useless div 6 3
This will return 2 as a quotient of 6 and 3

.It Pa ./useless sub 6 5
This will return 1 as a remainder of substraction of 5 from 6  

.Sh Authors
This script was designed and developed by Cylab Africa
.Pp 
picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_6194}
picoplayer@challenge:~$ Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
```

Respuesta: picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_6194}

## Notas
Explicación de la linea man -w useless | xargs zcat

### 1. `man -w useless`

Normalmente, el comando `man useless` te muestra el manual en pantalla. Pero al añadir la bandera **`-w`** (de _where_), le estás diciendo: _"No me muestres el manual, solo dime en qué parte del disco duro está guardado el archivo"_.

- **Resultado:** Te devolverá una ruta como `/usr/share/man/man1/useless.1.gz`.

### 3. `xargs`

Aquí está el truco. El comando que sigue (`zcat`) necesita que le digas el nombre de un archivo para trabajar. El problema es que el Pipe solo pasa "texto", no "instrucciones". **`xargs`** toma ese texto (la ruta que encontramos) y la convierte en un argumento real para que el siguiente comando pueda usarla. Es como el "pegamento" que permite que `zcat` sepa qué archivo abrir.

### 4. `zcat`

Como viste hace un momento, los archivos de manual están comprimidos en formato `.gz` para ahorrar espacio. Si usas `cat` normal, ves basura binaria. **`zcat`** es una versión especial de `cat` que **descomprime sobre la marcha** el archivo y te muestra el contenido en texto plano directamente en la terminal.

## Referencias
- Python Documentation – Built-in Functions  
    https://docs.python.org/3/library/functions.html#chr
    
- Python Documentation – bytes.fromhex()  
    https://docs.python.org/3/library/stdtypes.html#bytes.fromhex
    