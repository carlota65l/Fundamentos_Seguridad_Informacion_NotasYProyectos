## FANTASY CTF

## Descripcion
Play this short game to get familiar with terminal applications and some of the most important rules in scope for picoCTF.Connect to the program with netcat:
`$ nc verbal-sleep.picoctf.net 49508`
## Solucion
Se utilizó el comando:
nc verbal-sleep.picoctf.net 49508

🔍 Función:

- Permite conectarse a servicios remotos por TCP/UDP
- Muy usado en:
    - Retos CTF
    - Pentesting
    - Debugging de servicios

**picoCTF{m1113n1um_3d1710n_3b6c6fab}**

## Notas

El reto intenta “tentar” al usuario a romper reglas:

- Crear múltiples cuentas
- Buscar la flag en internet

👉 Pero la solución correcta es:

- Mantenerse dentro del marco permitido

#### Concepto de "Sanity Check"

En CTF:

- Es el reto más básico
- Sirve para validar que:
    - El entorno funciona
    - El usuario entiende cómo interactuar
#### Flujo de resolución

1. Conexión con `nc`
2. Lectura del contexto narrativo
3. Toma de decisiones correctas:
    - Registrar una sola cuenta
    - Jugar el reto en lugar de buscar la flag
4. Continuar el flujo hasta encontrar la flag

#### Lecciones importantes

- No siempre el camino “inteligente” es el correcto
- En ciberseguridad:
    - **la ética es tan importante como la técnica**
- Leer cuidadosamente es clave en retos CTF
## Referencias
- picoCTF  
    [https://picoctf.org/](https://picoctf.org/)
- Carnegie Mellon University  
    [https://www.cmu.edu/](https://www.cmu.edu/)
- Netcat  
    [https://linux.die.net/man/1/nc](https://linux.die.net/man/1/nc)
- Capture The Flag (CTF)  
    [https://ctftime.org/](https://ctftime.org/)