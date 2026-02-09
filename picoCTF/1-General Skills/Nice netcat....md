## Nice netcat...
## Descripcion
There is a nice program that you can talk to by using this command in a shell:$ nc wily-courier.picoctf.net 51972, but it doesn't speak English...
## Solucion
### solucion 1_ usando python

 el texto está **cifrado**, normalmente en **ROT13** (un cifrado por sustitución muy común en CTFs).

usando la terminal webshell:
```bash
BelovedCis-picoctf@webshell:~$ nc wily-courier.picoctf.net 51972
112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
102 
55 
97 
54 
101 
125 
10 
```

```bash
BelovedCis-picoctf@webshell:~$ echo "112 105 99 111 67 84 70 123 103 48 48 100 95 107 49 116 116 121 33 95 110 49 99 51 95 107 49 116 116 121 33 95 102 55 97 54 101 125" | awk '{for(i=1;i<=NF;i++) printf "%c",$i}'
picoCTF{g00d_k1tty!_n1c3_k1tty!_f7a6e}BelovedCis-picoctf@webshell:~$ 
```

Respuesta: 

picoCTF{g00d_k1tty!_n1c3_k1tty!_f7a6e}
## Notas
Texto raro + nc + “no English” →  ROT13
- Se estableció una conexión a un servicio remoto utilizando `netcat`.
    
- El servicio devolvió una secuencia de números separados por espacios.
    
- Se identificó que los valores correspondían a **ASCII decimal**.
    
- Se realizó la conversión de cada número a su carácter equivalente.
    
- El texto resultante reveló la flag del reto.

## Referencias
ASCII Table: [https://www.asciitable.com](https://www.asciitable.com)