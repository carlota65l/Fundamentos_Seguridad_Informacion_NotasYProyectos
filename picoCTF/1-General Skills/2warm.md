## 2warm
## Descripcion
Can you convert the number 42 (base 10) to binary (base 2)?
## Solucion
### solucion 1_ usando cyberChef
[https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')&input=MHg3MA](https://gchq.github.io/CyberChef/#recipe=From_Decimal('Space',false)To_Binary('Space',2)&input=NDI)
101010
picoCTF{101010}
### solucion 2_ usando python
```bash
BelovedCis-picoctf@webshell:~$ echo "obase=2; 42" | bc
101010
```

## Notas
cyberchef es una pagina queme permite decodificar en diferentes formatos
## Referencias
https://gchq.github.io/CyberChef