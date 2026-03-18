## MacroHard WeakEdge
## Descripcion
I've hidden a flag in this file. Can you find it?[Forensics_is_fun.pptm](https://challenge-files.picoctf.net/c_wily_courier/d78815176c19ddc85a1388233268d2f4c459fcbbaab197b4a29ebafc88294c54/Forensics_is_fun.pptm)
## Solucion
- Verificamos el tipo de archivo, para darnos cuenta que es un `.pptx` de `Power Point`:

`file "Forensics is fun.pptm"`

- Lo desempacampos con `unzip` dado que los archivos de office son en escencia archivos empaquetados:

`unzip "Forensics is fun.pptm"`

- Al desempacar pudimos percatarnos de la presencia del archivo `hidden`, nos movemos a la carpeta donde esta y lo mostramos

`cd ppt/slideMasters cat hidden`

- Es una cadena en `base64` con espacios, la decodificamos para ver la bandera

`cat hidden | tr -d ' ' | base64 -d`

**picoCTF{D1d_u_kn0w_ppts_r_z1p5}**
## Notas
### Archivos Office como contenedores

Office Open XML

- Funcionan como archivos comprimidos
    
- Permiten ocultar información en su estructura interna
### Codificación Base64

Base64

- Convierte datos binarios a texto
    
- Usado para ocultar o transportar información
### Análisis forense de archivos
Digital Forensics

- Inspección de estructuras internas
    
- Búsqueda de datos ocultos o no visibles

## Referencias
- Office Open XML Documentation
- Base64 Overview
- Manual de comandos Linux (`file`, `unzip`, `base64`)
- Recursos de análisis forense digital