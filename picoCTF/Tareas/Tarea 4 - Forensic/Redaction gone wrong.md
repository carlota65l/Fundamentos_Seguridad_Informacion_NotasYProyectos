## Redaction gone wrong
## Descripcion

Now you DON’T see me.This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?
## Solucion

1. - usar una utilidad como `pdftotext` para extraer todo el texto plano del documento y luego filtrarlo:
        
        Bash
        
        ```
        pdftotext Financial_Report_for_ABC_Labs.pdf
        cat Financial_Report_for_ABC_Labs.txt | grep picoCTF
        ```

Al revelar el texto que estaba debajo del cuadro negro en la sección final (cerca de _Expenses_ / Gastos), obtendrás el siguiente bloque de texto oculto:

Cost Benefit Analysis Credit Debit This is not the flag, keep looking Expenses from the **picoCTF{C4n_Y0u_S33_m3_fully}** 

## Notas

- **Censura de Documentos (Redaction):** Es el proceso legítimo de eliminar u ocultar de forma permanente información confidencial o sensible de un documento antes de su distribución pública (por ejemplo, nombres, números de cuenta, contraseñas).

- **Falsa Censura (Improper Redaction):** Ocurre cuando un usuario intenta censurar un documento simplemente alterando su apariencia visual (como resaltar texto en color negro o colocar una forma geométrica negra sobre las palabras) utilizando procesadores de texto comunes (como Word) y luego exportándolo a PDF.

- **Capas en archivos PDF:** El formato PDF (Portable Document Format) no es una simple imagen plana. Está compuesto por diferentes capas independientes de texto, vectores gráficas, imágenes y metadatos. Cuando se coloca un "cuadro negro" sobre un texto, el texto original sigue existiendo intacto en la capa de texto subyacente, permitiendo que la computadora lo lea y lo extraiga aunque el ojo humano no pueda verlo.
## Referencias

- **Sobre el diseño del formato PDF y sus capas:** Adobe Systems Incorporated. (s.f.). _PDF Reference, Sixth Edition, version 1.7_. Recuperado de la documentación oficial de Adobe.

- **Sobre cómo redactar/censurar correctamente:** Adobe Acrobat. (s.f.). _Quitar contenido confidencial de archivos PDF_. Recuperado de: [https://helpx.adobe.com/es/acrobat/using/removing-sensitive-content-pdfs.html](https://helpx.adobe.com/es/acrobat/using/removing-sensitive-content-pdfs.html)

- **Sobre los riesgos de la falsa censura (Lectura recomendada):** NSA (National Security Agency). (2005). _Hidden Data and Metadata in Adobe PDF Files: Publication Risks and Countermeasures_. (Un documento histórico y famoso donde la NSA advirtió sobre este exacto problema).

- **Sobre herramientas de extracción de texto:** Sitio oficial del proyecto Poppler (`pdftotext`). Recuperado de: [https://poppler.freedesktop.org/](https://poppler.freedesktop.org/)