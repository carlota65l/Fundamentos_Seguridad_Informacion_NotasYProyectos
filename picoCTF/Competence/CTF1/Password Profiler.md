## Password Profiler
## Descripcion
We intercepted a suspicious file from a system, but instead of the password itself, it only contains its SHA-1 hash. Using OSINT techniques, you are provided with personal details about the target. Your task is to leverage this information to generate a custom password list and recover the original password by matching its hash.Download the following files:[userinfo](https://challenge-files.picoctf.net/c_plain_mesa/3c16fb8e48ddae444f6840e81660a5a8cb2d30b69092b04f619d6ac34676a919/userinfo.txt): Contains the personal details.[hash](https://challenge-files.picoctf.net/c_plain_mesa/3c16fb8e48ddae444f6840e81660a5a8cb2d30b69092b04f619d6ac34676a919/hash.txt): Contains the SHA-1 hash of the password.[check_password](https://challenge-files.picoctf.net/c_plain_mesa/3c16fb8e48ddae444f6840e81660a5a8cb2d30b69092b04f619d6ac34676a919/check_password.py): Script to test passwords against the hash.
## Solucion

El archivo `userinfo.txt` contenía datos personales del objetivo, tales como:

- nombre
    
- apodo
    
- fecha de nacimiento
    
- mascota
    
- empresa
    
- información familiar
    

Este tipo de información suele utilizarse en contraseñas reales, por lo que es útil para ataques de **ingeniería social y OSINT**.
### Generación de un diccionario personalizado

Se utilizó la herramienta **CUPP**.

CUPP genera listas de contraseñas basadas en información personal del usuario.

Ejemplo de ejecución:

python3 cupp.py -i

El programa solicita información como:

- nombre
    
- apellido
    
- apodo
    
- fecha de nacimiento
    
- nombre de mascota
    
- empresa
    

Posteriormente genera un archivo con miles o millones de posibles contraseñas.
### Preparación del diccionario

El diccionario generado por CUPP fue renombrado a:

passwords.txt

Esto fue necesario porque el script `check_password.py` busca específicamente ese archivo.

### Comparación del hash

El script proporcionado usa la librería **hashlib** para calcular el hash SHA-1 de cada contraseña del diccionario.

Fragmento clave del código:

if hashlib.sha1(password.encode()).hexdigest() == target_hash:

El proceso consiste en:

1. Leer el hash objetivo desde `hash.txt`
    
2. Tomar cada contraseña del diccionario
    
3. Calcular su SHA-1
    
4. Compararlo con el hash objetivo
    

Cuando coincide, se recupera la contraseña original.


### Recuperación de la contraseña

Al encontrar una coincidencia, el script muestra la flag con el formato:

picoCTF{password}

Esto indica que la contraseña generó el mismo hash que el almacenado en el archivo.
**picoCTF{Aj_15901990}**
## Notas
El objetivo del ejercicio fue recuperar una contraseña a partir de su hash **SHA-1** utilizando técnicas de **OSINT y generación de diccionarios personalizados**.

En lugar de usar ataques de fuerza bruta tradicionales, se aprovechó información personal del objetivo para generar posibles contraseñas realistas.

#### Hash criptográfico

Un **hash criptográfico** es una función matemática que convierte datos de entrada en una cadena de longitud fija.

Características:

- irreversible
    
- mismo input → mismo hash
    
- pequeños cambios generan hashes totalmente diferentes
    

SHA-1 produce hashes de **160 bits**.
## Referencias
- **CUPP**  
    [https://github.com/Mebus/cupp](https://github.com/Mebus/cupp)
    
- **hashlib**  
    [https://docs.python.org/3/library/hashlib.html](https://docs.python.org/3/library/hashlib.html)