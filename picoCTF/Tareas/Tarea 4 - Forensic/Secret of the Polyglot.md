## Secret of the Polyglot
## Descripcion

The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/8/flag2of2-final.pdf).
## Solucion
 1. Descarga del artefacto wget https://artifacts.picoctf.net/c_titan/8/flag2of2-final.pdf 
 2. Análisis de cabeceras (Magic Bytes) file flag2of2-final.pdf # Salida esperada: PNG image data, 50 x 50, 8-bit/color RGBA...  
 3. Extracción de texto del PDF (Parte 2 de la flag) pdftotext flag2of2-final.pdf - | cat  
 4. Visualización de la imagen (Parte 1 de la flag) cp flag2of2-final.pdf flag.png 
 5. Abrir flag.png con cualquier visor gráfico

picoCTF{f1u3n7_1n_pn9_&_pdf_249d05c0}
## Notas

- **Anomalía de Extensión:** El archivo se entrega con extensión `.pdf`, pero las herramientas de análisis revelan una estructura dual.
    
- **Identificación por Magic Bytes:** Al utilizar el comando `file`, el sistema identifica el archivo como `PNG image data` basándose en los bytes iniciales, ignorando la extensión manual.
    
- **Esteganografía Básica:** La información se divide en dos capas de datos que no interfieren entre sí debido a cómo los visores de imágenes y lectores de PDF interpretan los finales de archivo (`IEND` en PNG vs `%%EOF` en PDF).
## Referencias

- **Gary Kessler’s File Signatures Table:** La base de datos definitiva para verificar "Magic Bytes". [https://www.garykessler.net/library/file_sigs.html](https://www.garykessler.net/library/file_sigs.html)
    
- **Ange Albertini (Ange007):** Investigador líder en "Funky File Formats" y archivos políglotas. Referencia: _Corksami Project_.
    
- **RFC 3778:** Especificaciones del tipo de medio `application/pdf`.
    
- **ISO 15948:** Estándar de la estructura de datos para Portable Network Graphics (PNG).