## Mini RSA
## Descripcion
What happens if you have a small exponent? There is a twist though, we padded the plaintext so that (M ** e) is just barely larger than N. Let's decrypt this:[values](https://challenge-files.picoctf.net/c_wily_courier/92ada45e45a764157d960bd97c862c9856d67a2526f3f372d17f72cdb3ea538e/values)

## Solucion

Buscamos un entero kkk tal que:

m3=kN+cm^3 = kN + cm3=kN+c

y que m3m^3m3 sea un **cubo perfecto**.

**picoCTF{e_sh0u1d_b3_lArg3r_92f4d5a5}**
## Notas
#### 1. Contexto: RSA

RSA es un sistema criptográfico basado en:

- Clave pública: (N,e)(N, e)(N,e)
- Clave privada: ddd

Cifrado:

c=memod  Nc = m^e \mod Nc=memodN

Descifrado:

m=cdmod  Nm = c^d \mod Nm=cdmodN

---

#### 2. Vulnerabilidad: exponente pequeño

Cuando:

- eee es pequeño (por ejemplo, e=3e = 3e=3)
- El mensaje mmm no está bien protegido (padding débil)


####  3. Idea del ataque (caso del ejercicio)

En este reto:

- e=3e = 3e=3
- El mensaje fue “rellenado” pero **no lo suficiente**

Entonces:

m3=kN+cm^3 = kN + cm3=kN+c

donde kkk es un entero pequeño.


#### Método práctico

1. Iterar valores de k=0,1,2,...k = 0,1,2,...k=0,1,2,...
2. Calcular:
    
    x=kN+cx = kN + cx=kN+c
3. Verificar si:
    
    x3 es entero\sqrt[3]{x} \text{ es entero}3x​ es entero
4. Convertir el resultado a texto (hex → ASCII)

## Referencias


- CryptoHack RSA (muy práctico)
- picoCTF → sección criptografía
- Wikipedia RSA