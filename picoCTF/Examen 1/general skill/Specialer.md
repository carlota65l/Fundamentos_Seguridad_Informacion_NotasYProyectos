## Specialer

## Descripcion
Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.`ssh -p 52551 ctf-player@saturn.picoctf.net`. The password is `fd7746b4`
## Solucion

### Shell restringida

Una **restricted shell** limita lo que el usuario puede ejecutar.

En este caso:

- No hay acceso a binarios del sistema (`/bin/ls`, `/bin/cat`)
- Solo se permiten comandos internos de Bash

**picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_38f5cc78}**

## Notas
- Uso de **builtins en Bash**
- Técnicas para evadir restricciones
- Globbing (`*`) como alternativa a `ls`
- Redirección de entrada (`<`)
- Exploración manual de sistemas Linux
## Referencias
- Writeup picoCTF Specialer – Medium
- Guía picoCTF General Skills
- Explicación de Bash Builtins – GNU
- [Globbing en Bash](https://tldp.org/LDP/abs/html/globbingref.html)
- [Restricted Shell Escapes](https://book.hacktricks.xyz/linux-hardening/privilege-escalation/escaping-from-limited-bash)