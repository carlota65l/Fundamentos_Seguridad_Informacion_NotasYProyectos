## basic-mod1
## Descripcion
We found this weird message being passed around on the servers, we think we have a working decryption scheme.Download the message [here](https://artifacts.picoctf.net/c/128/message.txt).Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.Wrap your decrypted message in the picoCTF flag format (i.e. `picoCTF{decrypted_message}`)
## Solucion

```python
# leemos el mensaje y quitamos espacios y dividimos en partes
data = open('message.txt','r').read().strip().split(' ')

print(data)
flag = ''

# recorremos el mensaje para decodificarlo
for c in data:
        char = int(c) % 37
        print(f'{c:<5} - {char:<5} - ',end='')
         # mapeamos a letras en codigo ascii sumando 65
        if char>=0 and char<=25:
                s = chr(char+65)
        # mapeamos a numeros en codigo ascii (48 - 26)
        elif char>=26 and char<=35: 
                s= chr(char+22)
        elif char==36:
                s = '_'
        flag += s
        print(s)
print(f'\n{flag}')
```

**picoCTF{R0UND_N_R0UND_B6B25531}**

## Notas
#### ¿Por qué 37?

Porque están codificando:

- 26 letras (A–Z)
- 10 dígitos (0–9)
- 1 símbolo (`_`)

Total = **37 caracteres**

El código no usa tablas, sino offsets:

- Letras → +65
- Números → +22
#### Suposición del formato

- El archivo debe tener números separados por espacios
- Si hay texto o símbolos → falla
## Referencias
#### ASCII

- Tabla ASCII estándar (para entender `chr()`)

Funciones usadas en Python

- `open()` → leer archivos
- `split()` → dividir strings
- `int()` → convertir a entero
- `chr()` → número → carácter