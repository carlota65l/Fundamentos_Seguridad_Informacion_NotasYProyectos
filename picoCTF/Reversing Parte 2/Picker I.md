## Picker I
## Descripcion
This service can provide you with a random number, but can it do anything else?Connect to the program with netcat:`$ nc saturn.picoctf.net 54490`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/515/picker-I.py).
## Solucion
Decodificar la flag
```python
>>> c = "0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x\
75 0x67 0x68 0x5f 0x36 0x65 0x30 0x34 0x34 0x34 0x30 0x64 0x7d".split()
>>> c
['0x70', '0x69', '0x63', '0x6f', '0x43', '0x54', '0x46', '0x7b', '0x34', '0x5f', '0x64', '0x31', '0x34', '0x6d', '0x30', '0x6e', '0x64', '0x5f', '0x31', '0x6e', '0x5f', '0x37', '0x68', '0x33', '0x5f', '0x72', '0x30', '0x75', '0x67', '0x68', '0x5f', '0x36', '0x65', '0x30', '0x34', '0x34', '0x34', '0x30', '0x64', '0x7d']
>>> [chr(int(x,16)) for x in c]
['p', 'i', 'c', 'o', 'C', 'T', 'F', '{', '4', '_', 'd', '1', '4', 'm', '0', 'n', 'd', '_', '1', 'n', '_', '7', 'h', '3', '_', 'r', '0', 'u', 'g', 'h', '_', '6', 'e', '0', '4', '4', '4', '0', 'd', '}']
>>> ''.join([chr(int(x,16)) for x in c])
'picoCTF{.....}'
>>> 
```

**picoCTF{4_d14m0nd_1n_7h3_r0ugh_ce4b5d5b}**
## Notas
- **Inyección de Código (Code Injection):** El fallo crítico de la aplicación es que confía ciegamente en lo que escribe el usuario. En lenguajes como Python, funciones como `eval()` o `exec()` toman una cadena de texto y la ejecutan como si fuera código del programa. Al no validar tu entrada, te permitió llamar a la función `win()` que el desarrollador dejó "escondida" en el código fuente.
    
- **Sistema Hexadecimal:** El resultado devuelto por el servidor (`0x70 0x69...`) está en sistema hexadecimal (base 16). El prefijo **`0x`** no forma parte del valor en sí, sino que es la convención universal en programación para indicarle a la computadora (y al lector) que los siguientes números están en formato hexadecimal.
    
- **Codificación ASCII:** Las computadoras no entienden letras, solo números. El estándar ASCII es un mapa que asigna un valor numérico a cada letra, número y símbolo. Por ejemplo, el valor hexadecimal `70` corresponde a la letra `p`, y el `69` a la `i`.
    
- **Netcat (`nc`):** Es la herramienta que usaste en la terminal para conectarte. Se le conoce como la "navaja suiza de las redes" y permite leer y escribir datos a través de conexiones de red (TCP/UDP). En los CTFs, es el estándar para interactuar con retos alojados en servidores remotos.
## Referencias
- **CyberChef:** Al igual que en el reto de la caja fuerte, esta herramienta web es tu mejor amiga. Para solucionar este tipo de respuestas, simplemente pegas la cadena y usas la receta **From Hex** (asegurándote de indicarle que el delimitador es `0x` o un espacio).
    
- **Decodificación con Python:** Como hacker o analista, a menudo querrás decodificar esto rápidamente desde tu propia terminal sin usar el navegador. Puedes abrir Python y usar un simple comando:
    
    > `print(bytes.fromhex('70 69 63 6f 43 54 46 7b').decode('ascii'))`
    
- **Tablas ASCII:** Tener una tabla ASCII a mano (buscando "ASCII Table" en la web) es muy útil para aprender a reconocer a simple vista ciertos patrones. Por ejemplo, siempre que veas `0x70 0x69 0x63 0x6f`, sabrás inmediatamente que dice `pico`.
    
- **OWASP (Prevención de Inyección de Código):** Si te interesa el lado de la defensa, te sugiero buscar información sobre _"Improper Control of Generation of Code"_ o _"Python eval() vulnerabilities"_. La forma correcta de programar esto habría sido usar un diccionario que mapee explícitamente cadenas de texto seguras a funciones permitidas, en lugar de ejecutar el texto directamente.