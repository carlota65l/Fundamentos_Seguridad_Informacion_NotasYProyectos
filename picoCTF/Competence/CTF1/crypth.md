## crypth
## Descripcion
no. no. that's Not TRUe. that's impossible! Download encryption script and public info. pista:This is a lattice based cryptosystem. Is there a lattice attack that allows you to compute the private key given the public information?
## Solucion

[*] Construyendo la matriz del retículo...
[*] Aplicando LLL para reducir la base...
[*] Buscando la clave privada candidata y descifrando el mensaje...

[+] ¡Éxito! Texto descifrado:
--> picoCTF{th4ts_s0_N0t_TRU3_0f84062d}
## Notas
- El algoritmo que analizamos es una implementación del criptosistema NTRU (N-th degree Truncated polynomial Ring Units).
    
- NTRU es un sistema criptográfico de clave pública basado en la dificultad de resolver problemas en retículos (lattices) y opera sobre álgebra de anillos de polinomios.
    
- Los parámetros públicos configurados para este ejercicio específico son $N = 48$, $p = 3$ y $q = 509$.
    
- La clave privada está conformada por dos polinomios ($f$ y $g$), los cuales se generan con coeficientes ternarios muy pequeños, típicamente en el conjunto $\{-1, 0, 1\}$.
    
- Durante la generación de claves, la clave pública $h$ se calcula mediante la congruencia $h \equiv p \cdot f^{-1}_q \cdot g \pmod q$.
    

**2. La Vulnerabilidad Matemática (El Ataque)**

- La seguridad teórica de NTRU radica en la extrema dificultad de encontrar vectores moderadamente cortos en retículos de alta dimensión.
    
- Sin embargo, en 1997, los criptógrafos Don Coppersmith y Adi Shamir propusieron un ataque de retículos diseñado específicamente para recuperar la clave privada de NTRU resolviendo el Problema del Vector Más Corto (SVP).
    
- Para llevar a cabo este ataque, el atacante construye el llamado "Retículo de Coppersmith-Shamir", el cual consiste en una matriz de dimensión $2N \times 2N$.
    
- La estructura de esta matriz está compuesta por cuatro bloques: la matriz identidad $I_N$, la matriz circulante generada por la clave pública $H$, una matriz nula (ceros) y la matriz $q I_N$.
    
- El fallo fatal en este reto es el tamaño de los parámetros: al utilizar un grado polinomial tan bajo como $N = 48$, el retículo generado tiene una dimensión de apenas $96 \times 96$.
    
- Con dimensiones tan reducidas, el algoritmo LLL (Lenstra-Lenstra-Lovász) es capaz de reducir la base del retículo y encontrar el vector más corto de manera extremadamente eficiente en tiempo polinomial, quebrando el sistema por completo.
## Referencias
https://sagecell.sagemath.org/