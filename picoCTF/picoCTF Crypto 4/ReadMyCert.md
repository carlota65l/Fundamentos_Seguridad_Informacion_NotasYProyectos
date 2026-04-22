## ReadMyCert
## Descripcion
How about we take you on an adventure on exploring certificate signing requestsTake a look at this CSR file [here](https://artifacts.picoctf.net/c/425/readmycert.csr).
## Solucion
### Solucion 1
- Ir a cybercheff, decodificar de base64 y se ve la bandera
### Solucion 2
- investigamos con IA como abrir un archivo con extension .csr en la consola
- lo mostramos y ahi viene la flag
```
openssl req -in readmycert.csr -noout -text
```
**picoCTF{read_mycert_693f7c03}**
## Notas
**¿Qué hace este comando?**

- **`req`**: Indica que estamos trabajando con una solicitud de firma de certificado (CSR).
    
- **`-text`**: Muestra el contenido del CSR en un formato legible para humanos.
    
- **`-noout`**: Evita que se imprima la versión codificada (texto plano) que no nos interesa leer directamente.
    
- **`-verify`**: Verifica la firma digital del archivo para asegurarse de que no esté corrupto.
    
- **`-in`**: Especifica el archivo de entrada que vas a leer.
## Referencias
https://gchq.github.io/CyberChef/#recipe=To_Base64('A-Za-z0-9%2B/%3D')&input=TUlJQ3B6Q0NBWThDQVFBd1BERW1NQ1FHQTFVRUF3d2RjR2xqYjBOVVJudHlaV0ZrWDIxNVkyVnlkRjgyT1RObQ0KTjJNd00zMHhFakFRQmdOVkJDa01DV04wWmxCc1lYbGxjakNDQVNJd0RRWUpLb1pJaHZjTkFRRUJCUUFEZ2dFUA0KQURDQ0FRb0NnZ0VCQVBwK1h1REIzWmttcmt2QXNndGpQK21qSWNZRFdmcHR1WnNKaWV1NmVSbDM5d2w0U2czOA0KKy9PZlkyNExWOXNObWdLeVRHdnBtQ2FVb1pNWWt2a3VsWVNvRnpFMHhxUEJvNmtydUxFeUl2cXFwQUZxUkgyYg0KbWllckxUNlJjS2dKSFlyL1Z0NlN3UDhOQ0Nhd0NydmhRNE5aY3VCNDlIci8yQWlHSHptZjg2L2xHL2MrbGhtSA0KZ3lxUGIxa0RnaHNWeGkvR05zOWk3QWduaVppa3FUOE9UcDBJTm1tQ2dadEpuMUpvNjE1SXUvdEZpQzhTZmhoZw0KUUhtVERMamd4MW9QMWt2WlYyUEU1VVVOL29DMDVadXA4ZjMxTGtzWFp3cGF6Wkt3WUMvTGJOOTZIZHFnVlE5Sw0KUzhlLzRJN01KUW1QbUxJc0xwM3NkTDJGaURHTUwzc21BaTBDQXdFQUFhQW1NQ1FHQ1NxR1NJYjNEUUVKRGpFWA0KTUJVd0V3WURWUjBsQkF3d0NnWUlLd1lCQlFVSEF3SXdEUVlKS29aSWh2Y05BUUVMQlFBRGdnRUJBT3hTUjhGcw0KVGRqZnU5ZTB2Uk5xS1dkMDlJU21ZRFFjM3FuU2JMUmxZWnlNSzRwZ3VBTHEzMTBoLzFuTmdVUldFU2JOSlBPcA0KRmtCV0cwWFdoV3lXUDdyVHF4by9wazlBS3gwVE5iSERyUzZLaUJuS1BxMG14alBac0gxTDd3TllEYzVPQU5EbA0KYnR2bjN6VDdsTW1zNnoxcU03eFVXWFI3Nm4yeEwvODFjZEY3MjVuQlowMG1XbVBXMFMxcFNtQTRFRUhDRWdOVw0KMHZXUXFzSURraTNnWWM0TkNtOE9Iang3OWtjd0Ura3N5YzZ2SGdNT3dzWW9PRkpueWF5aGwxNW9OLzN4N2hXMw0KRzF4b3ZQdXBBQnBmT1NOT2NUd2JnZnJmalVET0x4L3dpcnZqOUwxTjVFR0RoNEZPTGFSWkRzK3RNcmltR0JCUw0KekdVMTNCbnlrbVE1ak9RPQ0K&ieol=CRLF