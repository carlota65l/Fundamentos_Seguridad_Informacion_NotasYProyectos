## Obedient Cat
## Descripcion
This file has a flag in plain sight (aka "in-the-clear").[flag](https://challenge-files.picoctf.net/c_wily_courier/1a44abd1b8ea719b212d4645d5e9805a9db2e9062845609829d5d15e8e7d578c/flag).
## Solucion
### solucion 1_ usando python
#### La Bandera Encontrada

Al aplicar ese filtro al archivo, la línea resultante es la que contiene la respuesta:
```bash
belovedcis@DESKTOP-LNGE826:~$ cat flag
picoCTF{s4n1ty_v3r1f13d_9b8fa0bc}
```
Respuesta: s4n1ty_v3r1f13d_9b8fa0bc
picoCTF{s4n1ty_v3r1f13d_9b8fa0bc}
## Notas
**Linux:** se utilizo la terminal de picoCTF está basada en Ubuntu
**Eficiencia:** En escenarios más avanzados, se pueden combinar estos comandos. En lugar de descargar y luego buscar, se puede pasar la salida de un comando directamente a otro:

- **Ejemplo:** `cat flag | grep "picoCTF"`
## Referencias
