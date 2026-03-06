## SQLiLite
## Descripcion

Can you login to this website?Try to login [here](http://saturn.picoctf.net:60610/).
## Solucion
El reto consistía en acceder al sistema como **admin** explotando una vulnerabilidad de **inyección SQL** en el formulario de inicio de sesión.  
El sitio no validaba correctamente los datos introducidos por el usuario, lo que permitía modificar la consulta SQL enviada a la base de datos.
 
SELECT * FROM users 
WHERE username = 'admin' -- ' AND password = 'algo';

**picoCTF{L00k5_l1k3_y0u_solv3d_it_d3c660ac}**
## Notas

#### Riesgos de SQL Injection

Una vulnerabilidad SQLi puede permitir:

- bypass de autenticación
    
- lectura de bases de datos
    
- modificación de registros
    
- eliminación de datos
    
- ejecución de comandos dependiendo del motor
## Referencias

**Documentación SQL Injection**

- [https://portswigger.net/web-security/sql-injection](https://portswigger.net/web-security/sql-injection)

**SQLite Documentation**

- SQLite
- [https://www.sqlite.org/docs.html](https://www.sqlite.org/docs.html)