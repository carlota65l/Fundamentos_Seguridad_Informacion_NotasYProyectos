## information
## Descripcion
Files can always be changed in a secret way. Can you find the flag?[cat.jpg](https://challenge-files.picoctf.net/c_wily_courier/76e95e3e6ee69b4f82b3cea25051f5a9a5918b57809a1f90b29b06b776c73bc7/cat.jpg)

## Solucion
1. **Adquisición:** Se descargó el archivo de evidencia (`cat.jpg`) proporcionado por el reto.
    
2. **Análisis Estático:** Se inspeccionaron los metadatos del archivo utilizando `exiftool`.
    
3. **Identificación de Anomalías:** Se descubrió que el campo "License" contenía una cadena de texto inusual que no correspondía a un formato de licencia estándar (`cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9`).
    
4. **Procesamiento:** Se reconoció que la cadena estaba ofuscada en Base64. Se procedió a decodificarla utilizando utilidades de línea de comandos.
    
5. **Resolución:** La decodificación reveló exitosamente la bandera del reto:

**picoCTF{the_m3tadata_1s_modified}**
## Notas

- **ExifTool:** Una de las herramientas de software libre más potentes y versátiles para leer, escribir y editar metadatos en una amplia variedad de formatos de archivo. Fue crucial para revelar los campos ocultos de la imagen.

- **Terminal Linux (Comando `base64`):** Herramienta nativa de sistemas Unix/Linux utilizada para codificar y decodificar texto o archivos en el estándar Base64 de forma rápida a través de la línea de comandos.
## Referencias

- **Sobre ExifTool:** Harvey, P. (s.f.). _ExifTool by Phil Harvey_. Recuperado de: [https://exiftool.org/](https://exiftool.org/) _(Sitio oficial de la herramienta)._

- **Sobre Codificación Base64:** MDN Web Docs. (s.f.). _Base64_. Mozilla Foundation. Recuperado de: [https://developer.mozilla.org/es/docs/Glossary/Base64](https://developer.mozilla.org/es/docs/Glossary/Base64)

- **Herramienta alternativa para decodificar (Opcional para mencionar):** GCHQ. (s.f.). _CyberChef: The Cyber Swiss Army Knife_. Recuperado de: [https://gchq.github.io/CyberChef/](https://gchq.github.io/CyberChef/)