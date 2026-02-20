## Collaborative development
## Descripcion

My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/179/challenge.zip)

Este es un challenge de **forense en Git**. El programa de impresión de flags tenía "nuevas features" desarrolladas por el equipo, y cada feature estaba en su propia **branch de Git**. La flag estaba dividida en 3 partes, cada una almacenada en una branch diferente del repositorio.

## Solucion
### solucion 1_ usando python

#### Pasos de solución

**1. Descargar y descomprimir el archivo:**


```bash
wget https://artifacts.picoctf.net/c_titan/179/challenge.zip
unzip challenge.zip
cd drop-in
```

**2. Explorar las branches disponibles:**


```bash
git branch -a
```

Esto lista todas las ramas locales y remotas del repositorio.

**3. Inspeccionar cada branch:**


```bash
git checkout feature/part-1 && cat flag.py
git checkout feature/part-2 && cat flag.py
git checkout feature/part-3 && cat flag.py
```

`git checkout` cambia la rama activa, y `cat` muestra el contenido del archivo.

**4. Ensamblar la flag:** Concatenando los `print()` en orden: 
**picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_798f9981}**

## Notas

- Conocimiento básico de **Git** y su sistema de branches
- Capacidad de explorar el **historial y estructura** de un repositorio
- Entender que la información en distintas ramas **no se mezcla automáticamente** hasta un merge
- Navegación en línea de comandos Linux


Este ejercicio demuestra que los repositorios Git pueden contener información sensible distribuida en múltiples branches que no son visibles desde la rama principal. En un contexto de seguridad real, esto es relevante porque desarrolladores a veces almacenan credenciales, tokens o datos sensibles en branches "olvidadas" que permanecen en el historial del repositorio aunque nunca se hayan fusionado con `main`. Herramientas como `git log --all`, `git branch -a` y `git show` son esenciales para auditar repositorios en busca de este tipo de información.
## Referencias
- Documentación de `git branch`: [https://git-scm.com/docs/git-branch](https://git-scm.com/docs/git-branch)
- Documentación de `git checkout`: [https://git-scm.com/docs/git-checkout](https://git-scm.com/docs/git-checkout)
- Pro Git Book (libro gratuito, muy completo): [https://git-scm.com/book/en/v2](https://git-scm.com/book/en/v2)
- CTF101 - Forensics: [https://ctf101.org/forensics/overview/](https://ctf101.org/forensics/overview/)
- Introducción a Git para CTFs: [https://trailofbits.github.io/ctf/](https://trailofbits.github.io/ctf/)