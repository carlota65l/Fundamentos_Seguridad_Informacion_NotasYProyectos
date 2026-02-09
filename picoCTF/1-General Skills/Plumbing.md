## Plumbing
## Descripcion
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag?

**Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag?Connect to fickle-tempest.picoctf.net 64790.**

Objetivo: Capturar salida de un programa en ejecución y buscar una flag sin usar archivos.
## Solucion
### solucion 1_ usando python


 capturar la salida del proceso y buscar la flag mientras corre
 Conectarse con `nc` y filtrar la salida
Netcat + Pipes (CTF)
 
```bash
nc fickle-tempest.picoctf.net 64790 | grep picoCTF
picoCTF{digital_plumb3r_8c8f3412}
```
Respuesta: digital_plumb3r_8c8f3412

picoCTF{digital_plumb3r_8c8f3412}
## Notas
Netcat + Pipes (CTF)
Mucho texto + flag escondida → `| grep picoCTF`
Búsqueda más flexible
```bash
nc host puerto | grep -i pico
nc host puerto | grep -E "picoCTF|flag"
```

### Conceptos clave
- `nc` → conexión a servicios remotos
- `|` (pipe) → pasa la salida de un comando a otro
- `grep` → filtra texto en tiempo real
- No se crean archivos, se trabaja con streams

## Referencias
#ctf #linux #netcat #streams