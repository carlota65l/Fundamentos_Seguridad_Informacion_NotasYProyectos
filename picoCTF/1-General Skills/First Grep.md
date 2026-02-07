## First Grep
## Descripcion
Can you find the flag in the file? This would be really tedious to look through manually, something tells me there is a better way.The flag is in this [file](https://challenge-files.picoctf.net/c_fickle_tempest/d0b2e96347614d19414d591c946a1789fa8bd35487fcbfabf9437d0acfcaa503/file).
## Solucion
### solucion 1_ usando python
La bandera que encontramos, `TF{grep_is_good_to_find_things_e3C4b360}`, contiene el prefijo común que permite al comando identificar la línea exacta al instante.
```bash
grep "TF{" Reto
```
Respuesta: grep_is_good_to_find_things_e3C4b360
picoCTF{grep_is_good_to_find_things_e3C4b360}
## Notas
**Linux:** La terminal de picoCTF está basada en Ubuntu/Debian, donde **grep** es una utilidad estándar
**Eficiencia:** En retos de categoría "General Skills", a veces te dan archivos con miles de líneas. Usar **grep** te ahorra minutos de scroll innecesario.
## Referencias
