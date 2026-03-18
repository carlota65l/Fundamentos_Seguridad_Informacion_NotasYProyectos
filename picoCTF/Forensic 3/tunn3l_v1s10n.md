## tunn3l_v1s10n
## Descripcion
We found this file. Recover the flag.[tunn3l_v1s10n](https://challenge-files.picoctf.net/c_wily_courier/626df9feed926c1e1280804f5d87fde5576e266ff250a819a5528b0471b0f3f7/tunn3l_v1s10n)
## Solucion
### Identificación del tipo de archivo

Se utilizó:

file tunn3l_v1s10n

📌 Resultado:

- El sistema lo reconoce como `data`
    
- Indica que el archivo está corrupto o no tiene encabezado válido

### Análisis de metadatos

Se utilizó ExifTool:

exiftool tunn3l_v1s10n

📌 Resultado:

- Se detecta que el archivo corresponde a un formato BMP
    
- Confirma que el encabezado está dañado

**picoCTF{qu1t3_a_v13w_2020}**
## Notas
### Análisis de archivos binarios

- Inspección manual de bytes
    
- Uso de herramientas como `xxd`
    
### Estructura BMP

BMP file format

- Formato simple sin compresión
    
- Encabezado crítico para interpretación correcta
### Forense digital

Digital Forensics

- Recuperación de archivos dañados
    
- Análisis a bajo nivel
## Referencias
- ExifTool Documentation
- BMP file format Specification
- Herramienta `xxd` (manual de Linux)
- Recursos de análisis forense digital