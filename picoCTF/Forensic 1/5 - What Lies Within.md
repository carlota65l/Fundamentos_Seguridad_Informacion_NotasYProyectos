## What Lies Within
## Descripcion

## Solucion

### solucion 1_decodifcar

### El Concepto Clave: LSB (Least Significant Bit)

La técnica más común (y la que probablemente usa este ejercicio) es modificar el **Bit Menos Significativo**.

- **¿Cómo funciona?** Los colores en una imagen digital se definen por números (ej. Rojo: 255). Si cambias el último bit de ese número (de 255 a 254), el color cambia tan poquito que el ojo humano no lo nota, pero ese bit ahora guarda una pieza de tu mensaje secreto.
    
- **Capacidad:** Puedes esconder mucha información sin que la imagen "pese" más o se vea diferente.

**picoCTF{h1d1ng_1n_th3_b1t5}**

## Notas

### Herramientas de "Ataque" (Decodificación)

Cuando sospechas que una imagen tiene algo oculto, este es el orden de herramientas en Kali:

1. **`zsteg` (La navaja suiza para PNG/BMP):**
    
    - _Uso:_ `zsteg -a imagen.png`
        
    - _Por qué:_ Analiza todos los planos de bits automáticamente. Es la más efectiva para principiantes.
        
2. **`stegsolve` (Análisis Visual):**
    
    - _Uso:_ Es una herramienta JAR. La abres y pasas los filtros (Red 0, Green 0, Blue 0).
        
    - _Referencia:_ [StegSolve en GitHub](https://github.com/zardus/ctf-tools/blob/master/stegsolve/install).
        
3. **`steghide` (Para JPG con contraseña):**
    
    - _Uso:_ `steghide extract -sf imagen.jpg`
        
    - _Nota:_ A diferencia de LSB simple, esta suele pedir una clave.
        

### 3. Cómo esconder tu propio texto (Codificación)

#### Opción A: Usando `steghide` (Fácil y Seguro)

1. **Esconder:** `steghide embed -cf foto.jpg -ef secreto.txt`
    
    - `-cf`: Cover File (la foto).
        
    - `-ef`: Embed File (el texto).
        
2. Te pedirá una contraseña. La foto resultante se verá idéntica.
    

#### Opción B: Scripts de Python (Control Total)

Muchos profesionales usan scripts que manipulan la librería `PIL` (Pillow) para repartir los bits del texto entre los píxeles de la imagen.

## Referencias
- **[Aperi'Solve](https://www.aperisolve.com/):** Es una plataforma online que le pasas una imagen y le aplica `exiftool`, `zsteg`, `steghide` y `binwalk` de una sola vez. Es excelente para cuando estás atascado.

- **[CyberChef](https://gchq.github.io/CyberChef/):** La "navaja suiza" de la criptografía. Tiene una operación llamada "Extract LSB" que te permite jugar con los bits manualmente.
    
- **[CTF 101 - Steganography](https://www.google.com/search?q=https://ctf101.org/forensics/what-is-steganography/):** Una guía básica y muy clara sobre los tipos de esteganografía que existen.