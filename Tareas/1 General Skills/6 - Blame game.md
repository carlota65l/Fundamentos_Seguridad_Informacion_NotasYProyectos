## Blame game
## Descripcion

Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/156/challenge.zip)
## Solucion
### solucion 1_ usando python

Se utilizó el comando wget para descargar el archivo del reto desde el servidor:

```
wget https://artifacts.picoctf.net/c_titan/156/challenge.zip
```
Este comando descarga el archivo desde un servidor remoto al sistema local.

Extracción del archivo comprimido

Se utilizó el comando unzip para extraer el contenido:

unzip challenge.zip

Esto generó una carpeta llamada:

drop-in

Dentro de esta carpeta se encontró:

- message.py (archivo del programa)
    
- .git (repositorio Git oculto)
    

La presencia de la carpeta `.git` indica que el proyecto utiliza el sistema de control de versiones Git.

Acceso al repositorio

Se ingresó a la carpeta del repositorio:

cd drop-in

---

#### Análisis del historial de commits

Se utilizó el siguiente comando:

git log

Este comando muestra el historial completo de cambios realizados en el proyecto, incluyendo:

- ID del commit
    
- Autor
    
- Fecha
    
- Mensaje del commit
    

Esto permite identificar quién realizó modificaciones.

Para mostrar únicamente los nombres de los autores, se utilizó:

git log --pretty=format:"%h - %an"

Este comando muestra:

- Hash corto del commit
- Nombre del autor

**Respuesta: picoCTF{@sk_th3_1nt3rn_d2d29f22}**



## Notas

Git almacena todos los cambios en el directorio oculto `.git`  
• Cada commit tiene un identificador hash único  
• git log muestra el historial de cambios  
• git blame muestra quién modificó cada línea  
• unzip permite extraer archivos comprimidos  
• wget permite descargar archivos desde internet  
• El análisis de repositorios es una técnica común en CTF
## Referencias
Libro recomendado:  
Pro Git — Scott Chacon y Ben Straub

Documentación git blame:  
[https://git-scm.com/docs/git-blame](https://git-scm.com/docs/git-blame)

Documentación git log:  
[https://git-scm.com/docs/git-log](https://git-scm.com/docs/git-log)

Documentación wget:  
[https://www.gnu.org/software/wget/manual/wget.html](https://www.gnu.org/software/wget/manual/wget.html)

Documentación unzip:  
[https://linux.die.net/man/1/unzip](https://linux.die.net/man/1/unzip)