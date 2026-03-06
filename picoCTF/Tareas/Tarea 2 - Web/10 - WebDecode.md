## WebDecode
## Descripcion


## Solucion


En este reto de picoCTF se utilizó el **Web Inspector del navegador** para analizar los archivos que componen la página web. Dentro de uno de los archivos cargados por el sitio se encontró una cadena aparentemente ilegible.

Tras analizarla, se identificó que estaba **codificada en Base64**, un esquema de codificación que convierte datos binarios en texto ASCII utilizando 64 caracteres. Este método no es un mecanismo de seguridad, sino únicamente una forma de representar datos en texto.

Al decodificar la cadena Base64 utilizando herramientas como el comando `base64` en Linux o decodificadores en línea, se obtuvo la bandera del reto.

La pista dice que **puede estar codificada**, y se encontro esto:

**cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMDJjZGNiNTl9**

Eso suele ser **Base64**. Puedes decodificarlo con:

echo "texto" | base64 -d

o en mi caso utilice cyberChef 

**picoCTF{web_succ3ssfully_d3c0ded_02cdcb59}**
## Notas

- **Base64** es un método de **codificación**, no de cifrado.
    
- Se utiliza comúnmente para:
    
    - enviar datos binarios en HTTP
        
    - correos electrónicos (MIME)
        
    - tokens y datos web.
        
- Cualquier dato enviado al navegador **puede ser analizado por el usuario**.
    
- Las herramientas de desarrollador permiten inspeccionar:
    
    - HTML
        
    - CSS
        
    - JavaScript
        
    - recursos cargados.
## Referencias

https://gchq.github.io/CyberChef/