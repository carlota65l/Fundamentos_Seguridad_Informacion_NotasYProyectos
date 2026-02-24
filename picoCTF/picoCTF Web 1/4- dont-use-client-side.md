## dont-use-client-side
## Descripcion

Can you break into this super secure portal?http://fickle-tempest.picoctf.net:55369
## Solucion


### solucion 1_ codigo fuente

#### Dato clave

split = 4

Entonces cada bloque es de **4 caracteres**.

Los `substring(inicio, fin)` quedan así:

|Expresión|Posiciones|Texto|
|---|---|---|
|(0,4)|0–3|pico|
|(4,8)|4–7|CTF{|
|(8,12)|8–11|no_c|
|(12,16)|12–15|lien|
|(16,20)|16–19|ts_p|
|(20,24)|20–23|lz_2|
|(24,28)|24–27|eb02|
|(28,32)|28–31|b45}|



##### Ahora los ordenamos en orden correcto

Concatenando desde posición 0 hasta 32:

pico  
CTF{  
no_c  
lien  
ts_p  
lz_2  
eb02  
b45}


##### Bandera completa

picoCTF{no_clients_plz_2eb02b45}

## Notas

`substring(0, split) substring(split, split*2) substring(split*2, split*3) substring(split*3, split*4) substring(split*4, split*5) substring(split*5, split*6) substring(split*6, split*7) substring(split*7, split*8)````

## Referencias


- cliente - servidor : [https://www.educative.io/answers/client-side-vs-server-side](https://www.educative.io/answers/client-side-vs-server-side "https://www.educative.io/answers/client-side-vs-server-side")
- firefox depurador: [https://firefox-source-docs.mozilla.org/devtools-user/debugger/index.html](https://firefox-source-docs.mozilla.org/devtools-user/debugger/index.html "https://firefox-source-docs.mozilla.org/devtools-user/debugger/index.html")
