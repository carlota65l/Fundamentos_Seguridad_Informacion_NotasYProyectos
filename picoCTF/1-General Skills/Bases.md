## Bases
## Descripcion
What does this bDNhcm5fdGgzX3IwcDM1 mean? I think it has something to do with bases.
#### Qué es `bDNhcm5fdGgzX3IwcDM1`?

Eso es **Base64**.  
Es un método de codificación muy común en CTFs (y en la vida real).
## Solucion
### solucion 1_ usando cyberChef
https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=YkROaGNtNWZkR2d6WDNJd2NETTE
Respuesta: l3arn_th3_r0p35
picoCTF{l3arn_th3_r0p35}
### solucion 2_ usando python
```bash
BelovedCis-picoctf@webshell:~$ echo "bDNhcm5fdGgzX3IwcDM1" | base64 --decode
l3arn_th3_r0p35
```

## Notas
cyberchef es una pagina queme permite decodificar en diferentes formatos
## Referencias
https://gchq.github.io/CyberChef