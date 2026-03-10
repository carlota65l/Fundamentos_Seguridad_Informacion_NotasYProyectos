## extensions
## Descripcion

## Solucion

### solucion 1 txt a png
**picoCTF{now_you_know_about_extensions}**

#### Cómo verlos en tu terminal de Kali

Si tienes una imagen llamada `secreto.png`, puedes verificar sus magic bytes instantáneamente con este comando:

```
xxd secreto.png | head -n 1
```

**Deberías ver algo como esto:** `00000000: 8950 4e47 0d0a 1a0a ...`

#### El truco del CTF (Reparación)

Si en un reto te dan un archivo que supuestamente es un PNG pero no abre, lo primero que debes hacer es:

1. Abrirlo con `hexeditor secreto.png`.
    
2. Observar los primeros 8 bytes. Si ves algo como `41 41 41 41...` (puras letras A), el autor del reto los borró.
    
3. **Sobrescríbelos** manualmente con `89 50 4E 47 0D 0A 1A 0A`.
    
4. Guarda (`Ctrl+O`) y sal (`Ctrl+X`).
    
5. ¡La imagen ahora debería abrirse mágicamente!

## Notas

- **Fíjate en el nombre del archivo:** En tu visor de imágenes dice `glag.png`. Es un juego de palabras del autor del reto para recordarte que no importa cómo se llame el archivo (o si tiene la extensión mal puesta), lo que importa es el contenido real.
    
- **Cuidado al copiar:** Asegúrate de no incluir espacios extra al final cuando la pegues en la plataforma de picoCTF, ya que a veces da error por eso.
## Referencias
