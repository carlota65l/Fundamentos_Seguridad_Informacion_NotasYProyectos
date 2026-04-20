## b00tl3gRSA3
## Descripcion
Why use p and q when I can use more?Connect with nc fickle-tempest.picoctf.net 49270.

## Solucion
### b00tl3gRSA3 
```
- El valor de n es pequeño, pero no lo suficiente para factorizar de manera simple
- Por lo que encontramos factores multiples y tn con :  https://www.alpertron.com.ar/ECM.HTM
- Se decodifica c y se obtiene m que es la flag
```
```python
c = ...
n = ... 
e = ...

# obtenido de https://www.alpertron.com.ar/ECM.HTM
tn = ...

d = pow(e, -1, tn)
m = pow(c, d, n)

flag = bytes.fromhex(hex(m)[2:]).decode()

print(flag)
```

**picoCTF{too_many_fact0rs_3023548}**
## Notas
- **Extracción de datos:** Se capturó el tráfico de red mediante `nc` para extraer el criptograma ($c$), el módulo público ($n$) y el exponente público ($e$).
    
- **Análisis de vulnerabilidad:** Basado en la pista del título y el análisis del tamaño de $n$, se infirió que $n$ era altamente factorizable al estar compuesto por múltiples raíces pequeñas.
    
- **Factorización del módulo:** Se procesó el valor de $n$ utilizando el algoritmo ECM (Método de Curvas Elípticas) para extraer todos sus factores primos individuales.
    
- **Cálculo del Totiente:** Se restó el valor de **1** a cada factor primo encontrado y se multiplicaron todos los resultados entre sí para hallar $\phi(n)$.
    
- **Generación de clave privada:** Mediante aritmética modular en Python, se calculó el inverso multiplicativo de $e$ módulo $\phi(n)$ para obtener la clave privada ($d$).
    
- **Descifrado final:** Se elevó el criptograma $c$ a la potencia de $d$ módulo $n$, revelando el mensaje en un bloque de enteros, el cual fue decodificado a bytes (UTF-8) para extraer la _flag_.

## Referencias
- **Calculadora de Alpertron:** Herramienta web desarrollada por Darío Alpern. Utiliza subprocesos en JavaScript para ejecutar algoritmos avanzados como la Criba Cuadrática (SIQS) y el Método de Curvas Elípticas (ECM) directamente en el navegador. Ideal para CTFs. ([https://www.alpertron.com.ar/ECM.HTM](https://www.alpertron.com.ar/ECM.HTM))
    
- **YAFU (Yet Another Factoring Utility):** Software de línea de comandos para Linux. Es el estándar de la industria en CTFs para automatizar el rompimiento de enteros grandes. Ajusta dinámicamente el algoritmo matemático a usar dependiendo de la topología del número.
    
- **FactorDB:** Base de datos comunitaria que almacena las descomposiciones factoriales de millones de números. Es la primera línea de consulta recomendada antes de gastar recursos de hardware en factorizaciones largas. ([http://factordb.com/](http://factordb.com/))
    
- **PyCryptodome:** Módulo de criptografía para Python. Facilita las operaciones inversas y la manipulación de bloques de datos (como la función `long_to_bytes`).
    
- **RFC 3447 (PKCS #1):** Documentación técnica oficial de la IETF sobre los estándares de criptografía RSA, que incluye las especificaciones exactas sobre cómo operar RSA de forma legítima con más de dos factores primos (Multi-prime).