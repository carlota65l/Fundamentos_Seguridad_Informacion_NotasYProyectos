## Super SSH
## Descripcion

Using a Secure Shell (SSH) is going to be pretty important.

Can you `ssh` as `ctf-player` to `titan.picoctf.net` at port `52138` to get the flag?You'll also need the password `f3b61b38`. If asked, accept the fingerprint with `yes`.If your device doesn't have a shell, you can use: [https://webshell.picoctf.org](https://webshell.picoctf.org/)If you're not sure what a shell is, check out our Primer: [https://primer.picoctf.com/#_the_shell](https://primer.picoctf.com/#_the_shell)
## Solucion

utilizando el protocolo SSH (Secure Shell). El objetivo principal es autenticar el acceso con credenciales específicas (usuario, contraseña y puerto) y recuperar un archivo o mensaje denominado "flag", el cual confirma el acceso exitoso al sistema remoto.

Este tipo de actividad forma parte de ejercicios prácticos de ciberseguridad orientados al aprendizaje del acceso remoto seguro, autenticación en sistemas Linux y uso de la terminal como herramienta fundamental de administración y análisis.

El servidor remoto utilizado fue:

- Host: titan.picoctf.net
    
- Puerto: 52138
    
- Usuario: ctf-player
    
- Contraseña: f3b61b38
    

La conexión se realizó mediante una interfaz de línea de comandos (shell), lo que permitió interactuar directamente con el sistema remoto.
### solucion 1_ usando python


 
```bash
BelovedCis-picoctf@webshell:~$ ssh ctf-player@titan.picoctf.net -p 52138
The authenticity of host '[titan.picoctf.net]:52138 ([3.139.174.234]:52138)' can't be established.
ED25519 key fingerprint is SHA256:4S9EbTSSRZm32I+cdM5TyzthpQryv5kudRP9PIKT7XQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[titan.picoctf.net]:52138' (ED25519) to the list of known hosts.
ctf-player@titan.picoctf.net's password: 
Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_3e293eea}
Connection to titan.picoctf.net closed.
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{s3cur3_c0nn3ct10n_3e293eea}

## Notas

- SSH (Secure Shell) es un protocolo de red que permite el acceso remoto seguro a otros sistemas mediante cifrado.
    
- El puerto especificado (-p 52138) indica el canal de comunicación utilizado por el servicio SSH.
    
- La autenticación mediante usuario y contraseña es uno de los métodos más comunes de control de acceso.
    
- La aceptación del fingerprint permite verificar la identidad del servidor y prevenir ataques de intermediario (Man-in-the-Middle).
    
- Los comandos utilizados (ls, cat) son comandos básicos del sistema operativo Linux utilizados para listar y visualizar archivos.
    

Importancia en ciberseguridad:

Este ejercicio es fundamental porque enseña uno de los métodos más utilizados por administradores de sistemas, profesionales de ciberseguridad y especialistas en redes para:

- Administrar servidores remotamente
    
- Analizar sistemas comprometidos
    
- Obtener evidencia digital
    
- Realizar auditorías de seguridad
## Referencias
picoCTF. (s.f.). Plataforma educativa de ciberseguridad. Desarrollada por Carnegie Mellon University.
Barrett, D. J., Silverman, R. E., & Byrnes, R. G. (2005). SSH, The Secure Shell: The Definitive Guide. O'Reilly Media.
Stallings, W. (2017). Network Security Essentials: Applications and Standards. Pearson.
Linux Manual Pages. Comandos SSH, ls y cat. Sistema operativo Linux.