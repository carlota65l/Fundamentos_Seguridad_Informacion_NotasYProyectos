## what's a net cat?
## Descripcion
Using netcat (nc) is going to be pretty important. Can you connect to fickle-tempest.picoctf.net at port 63540 to get the flag?

## Solucion
### solucion 1_ usando python


Conectarte por TCP a:

- **Host:** `fickle-tempest.picoctf.net`
    
- **Puerto:** `63540`
    

Usando **nc (netcat)** para que el servidor te entregue la **flag**.
```bash
BelovedCis-picoctf@webshell:~$ nc fickle-tempest.picoctf.net 63540
You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_0d33dA2C}
```
Respuesta: nEtCat_Mast3ry_0d33dA2C
picoCTF{nEtCat_Mast3ry_0d33dA2C}
## Notas
nc fickle-tempest.picoctf.net 63540

## Referencias
