##  Pixelated
## Descripcion
I have these 2 images, can you make a flag out of them?[scrambled1.png](https://challenge-files.picoctf.net/c_wily_courier/3dced65f7a857f7a28f538da0f98fdceca989646f69d4651133b5c04590b0b0d/scrambled1.png) [scrambled2.png](https://challenge-files.picoctf.net/c_wily_courier/3dced65f7a857f7a28f538da0f98fdceca989646f69d4651133b5c04590b0b0d/scrambled2.png)
## Solucion
## Pixelated

### Solución 1 -  con `stegsolve`
- Descargamos `stegsolve` : 
```
cd /opt
sudo wget http://www.caesum.com/handbook/Stegsolve.jar -O stegsolve.jar
sudo chmod +x stegsolve.jar
java -jar /opt/stegsolve.jar 
```
- Abrimos la primer imagen
    - `File - Open`
- La combinamos con la segunda 
    - `Analyse - Image Combiner`
- Usamos los iconos de flecha en la parte de abajo para elegir el tipo de combinación hasta encontrar AND 
- Opcionalmente grabamos el archivo con la bandera
### Solución 2 - con  python `PIL`
```python
from PIL import Image
import numpy as np

imagen1 = np.asarray( Image.open('scrambled1.png') )
imagen2 = np.asarray( Image.open('scrambled2.png') )

data = imagen1 + imagen2

nueva = Image.fromarray(data)
nueva.save("out.png", "PNG")
```

**picoCTF{8cdf93c3}**
## Notas
**Visual cryptography** is a [cryptographic](https://en.wikipedia.org/wiki/Cryptography "Cryptography") technique which allows visual information (pictures, text, etc.) to be encrypted in such a way that the decrypted information appears as a visual image.
## Referencias
https://en.wikipedia.org/wiki/Visual_cryptography