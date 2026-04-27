##  EVEN RSA CAN BE BROKEN???
## Descripcion
This service provides you an encrypted flag. Can you decrypt it with just N & e?Connect to the program with netcat:`$ nc verbal-sleep.picoctf.net 62634`The program's source code can be downloaded [here](https://challenge-files.picoctf.net/c_verbal_sleep/c798cbe85b3e431345406f393827b9b905481b5fcd6d4b4a845527ee0602da9b/encrypt.py).
## Solucion
````
```
def egcd(a,b):
    if a==0:
        return (b,0,1)
    g,y,x = egcd(b%a,a)
    return (g, x-(b//a)*y, y)

def modinv(a,m):
    g,x,y = egcd(a,m)
    return x%m

def long_to_bytes(n):
    h=hex(n)[2:]
    if len(h)%2: h='0'+h
    return bytes.fromhex(h)

N=int(input())
e=int(input())
c=int(input())

p=N//2
phi=p-1
d=modinv(e,phi)

m=pow(c,d,N)
print(long_to_bytes(m).decode())
````

**picoCTF{tw0_1$_pr!m341c6ed35}**
## Notas
- Criptografía asimétrica
- Generación correcta de primos en RSA
- Factorización trivial por errores de implementación
- Cálculo de función totiente de Euler
- Inverso modular
- Ataques por mala aleatoriedad (“How much do we trust randomness?”)
## Referencias
- Introduction to Modern Cryptography  
    Capítulos sobre RSA y seguridad de generación de claves.
https://brilliant.org/wiki/extended-euclidean-algorithm/