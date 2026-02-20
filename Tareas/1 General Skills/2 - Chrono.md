##   Chrono
## Descripcion
How to automate tasks to run at intervals on linux servers?Use ssh to connect to this server:

```
Server: saturn.picoctf.net
Port: 58378
Username: picoplayer 
Password: pYkku7iMsS
```

## Solucion
### solucion 1_ usando python

funcionamiento del sistema de automatización de tareas en Linux mediante el servicio cron. A través del acceso remoto por SSH y la inspección del archivo `/etc/crontab`, se identificó la ubicación donde se programan las tareas automáticas del sistema. Este reto resalta la importancia de la enumeración en seguridad informática y evidencia cómo los archivos de configuración pueden contener información sensible si no están correctamente protegidos.
 
```bash
BelovedCis-picoctf@webshell:~$ ssh -p 58378 picoplayer@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:58378 ([13.59.203.175]:58378)' can't be established.
ED25519 key fingerprint is SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:58378' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.8.0-1044-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

picoplayer@challenge:~$ cat /etc/crontab
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_7754e199}
picoplayer@challenge:~$ Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{Sch3DUL7NG_T45K3_L1NUX_7754e199}


## Notas
### Automatización en servidores

Cron es una herramienta esencial para la administración de sistemas porque permite ejecutar tareas sin intervención humana.

Sin embargo, una mala configuración puede introducir riesgos de seguridad.

---

Seguridad en SSH

El mensaje de autenticidad del host demuestra el uso de:

- Criptografía de clave pública

- Verificación de identidad del servidor

- Prevención de ataques MITM
---

Este reto refuerza que la fase más importante en un pentest es:
**La enumeración de archivos del sistema**
Muchas veces la información sensible se encuentra accesible sin necesidad de explotación.

## Referencias
#### Administración de sistemas Linux

- Nemeth, E. — _UNIX and Linux System Administration Handbook_
- Sobell, M. — _Practical Guide to Linux Commands_
- Linux Manual Pages — crontab(5)
- HackTricks — Linux Privilege Escalation via Cron
- NIST — Security Configuration Guidelines