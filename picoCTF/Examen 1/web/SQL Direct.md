## SQL Direct

## Descripcion
Connect to this PostgreSQL server and find the flag!

Additional details will be available after launching your challenge instance.
## Solucion

**Inicia la conexión** Ejecuta tu comando en la terminal. Cuando te pida el _Password_, escribe `postgres` y presiona Enter (nota: al escribir contraseñas en la terminal, no se ven los caracteres, pero sí se están registrando).

Bash

```
psql -h saturn.picoctf.net -p 55928 -U postgres pico
```

**2. Lista las tablas** Una vez dentro, el prompt de tu terminal cambiará a algo como `pico=#`. Ahora necesitas ver qué tablas están guardadas ahí. En PostgreSQL, el atajo para mostrar las tablas (Display Tables) es:

SQL

```
\dt
```

**3. Encuentra la tabla correcta** El comando anterior imprimirá una lista. Revisa la columna de "Nombre" o "Name". Deberías ver una tabla con un nombre que destaque, algo evidente como `flags`, `flag`, o un nombre misterioso.

**4. Lee el contenido de esa tabla** Digamos que encontraste una tabla que se llama `flags`. Para volcar su contenido y ver qué hay dentro, tienes que usar una consulta SQL básica. Solo escribe esto (¡no olvides el punto y coma al final!):

SQL

```
SELECT * FROM flags;
```

**picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}**

## Notas
Estos comandos son exclusivos de la consola `psql` (no son lenguaje SQL universal) y siempre empiezan con una barra invertida `\`.

- `\dt`: Muestra (**d**isplay) todas las **t**ablas de la base de datos actual. _Es tu herramienta de reconocimiento principal en estos retos._
    
- `\l`: Muestra (**l**ist) todas las bases de datos disponibles en el servidor.
    
- `\q`: Cierra la conexión y sale (**q**uit) del programa.
## Referencias
- [W3Schools - SQL Tutorial](https://www.w3schools.com/sql/): Es excelente para repasar rápidamente cómo hacer `SELECT`, `INSERT`, o filtrar con `WHERE`.
    
- [SQL Murder Mystery](https://mystery.knightlab.com/): Un juego interactivo en el navegador donde usas sentencias SQL reales para resolver un crimen. Es muy divertido y te entrena la lógica mental para los CTFs.