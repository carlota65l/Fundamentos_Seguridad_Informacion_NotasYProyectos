## vault-door-1
## Descripcion
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: [VaultDoor1.java](https://challenge-files.picoctf.net/c_fickle_tempest/eb2eaca69cb975c96a289b4db182ed439cf7f6bc542b135b8a9a1e9834c068c1/VaultDoor1.java)
## Solucion

- Examinamos el código fuente en Java que se nos da
- De la función `checkPassword` copiamos a un archivo, las lineas con `password.charAt` 
- Agregamos 0s a las cantidades para hacerlas de dos dígitos y poderlas ordenar
- Ordenamos  
```bash
cat flag | sort
```
- Imprimimos 3a columna
```bash
cat flag | sort | awk '{print($3)}'
```
- Quitamos comilla que abre y cierra
```bash
cat flag | sort | awk '{print($3)}' | tr -d "\'"  
```
- Quitamos saltos de linea
```bash
cat flag | sort | awk '{print($3)}' | tr -d "'" | tr -d "\n"
```

**picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_29e8d8}**
## Notas
El método charAt() en Java, perteneciente a la clase `String`, devuelve el carácter (`char`) situado en un índice específico dentro de una cadena. Los índices comienzan en 0 y terminan en `longitud() - 1`. Si se utiliza un índice negativo o fuera de rango, lanza una excepción `StringIndexOutOfBoundsException`
## Referencias
https://www.w3schools.com/java/ref_string_charat.asp