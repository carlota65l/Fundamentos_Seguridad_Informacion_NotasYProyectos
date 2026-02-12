## repetitions
## Descripcion
Can you make sense of this file?Download the file [here](https://artifacts.picoctf.net/c/475/enc_flag).
## Solucion
### solucion 1_ usando python



 
```bash
BelovedCis-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/475/enc_flag
--2026-02-12 01:51:43--  https://artifacts.picoctf.net/c/475/enc_flag
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.170.131.33, 3.170.131.72, 3.170.131.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.170.131.33|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 349 [application/octet-stream]
Saving to: 'enc_flag'

enc_flag              100%[=========================>]     349  --.-KB/s    in 0s      

2026-02-12 01:51:44 (277 MB/s) - 'enc_flag' saved [349/349]

BelovedCis-picoctf@webshell:~$ cat enc_flag
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbFZrTTBKVVZXcE9VazFXV2toT1dHUllDbUY2UWpSWk1GWlhWa2RHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==
BelovedCis-picoctf@webshell:~$ cat enc_flag | base64 -d
VjFSQ2EyTXlSblJUV0dSVllrWmFWRmx0TlZOalJtUlhZVVU1YVZKVVZuaFdWekZoWVZkR2NrNVVX
bUZTVmtwUVdWUkdibVZXVm5WUgpiSEJzWVRCd2VWVXhXbXBOUlRWSFdqTnNWZ3BYUjFKeVZGZHdW
MlZzVWxaVmJFNW9UVVJDTlZaWE1XRlVkM0JUVWpOUk1WWkhOWGRYCmF6QjRZMFZXVkdGdGVFVlhi
bTkzVDFWT2JsQlVNRXNLCg==
BelovedCis-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d
V1RCa2MyRnRTWGRVYkZaVFltNVNjRmRXYUU5aVJUVnhWVzFhYVdGck5UWmFSVkpQWVRGbmVWVnVR
bHBsYTBweVUxWmpNRTVHWjNsVgpXR1JyVFdwV2VsUlZVbE5oTURCNVZXMWFUd3BTUjNRMVZHNXdX
azB4Y0VWVGFteEVXbm93T1VOblBUMEsK
BelovedCis-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d | base64 -d
WTBkc2FtSXdUbFZTYm5ScFdWaE9iRTVxVW1aaWFrNTZaRVJPYTFneVVuQlpla0pyU1ZjME5GZ3lV
WGRrTWpWelRVUlNhMDB5VW1aTwpSR3Q1VG5wWk0xcEVTamxEWnowOUNnPT0K
BelovedCis-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d | base64 -d | base64 -d
Y0dsamIwTlVSbnRpWVhObE5qUmZiak56ZEROa1gyUnBZekJrSVc0NFgyUXdkMjVzTURSa00yUmZO
RGt5TnpZM1pESjlDZz09Cg==
BelovedCis-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d
cGljb0NURntiYXNlNjRfbjNzdDNkX2RpYzBkIW44X2Qwd25sMDRkM2RfNDkyNzY3ZDJ9Cg==
BelovedCis-picoctf@webshell:~$ cat enc_flag | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_492767d2}

```

Respuesta: picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_492767d2}

## Notas

Al descargar el archivo `enc_flag` se observó que:

- El contenido estaba compuesto únicamente por:
    
    - Letras mayúsculas y minúsculas
        
    - Números
        
    - Símbolos `+`, `/`
        
    - Terminación en `=` o `==`
        

Estas características son típicas de una cadena codificada en **Base64**.

¿Qué es Base64?
Base64 es un esquema de codificación que convierte datos binarios en texto ASCII utilizando un conjunto de 64 caracteres:
`A–Z a–z 0–9 + /`
Se utiliza comúnmente para:

- Transmisión segura de datos
    
- Correos electrónicos (MIME)
    
- Archivos embebidos
    
- Ofuscación básica en retos CTF
    

**Importante: Base64 no es cifrado, es solo codificación.**


 Procedimiento de Decodificación

Se utilizó el comando:

`base64 -d archivo`

Durante el análisis se observó que, tras decodificar una vez, el resultado seguía teniendo formato Base64.

Esto indica que el archivo estaba **codificado múltiples veces**.

Se repitió el proceso:

`base64 -d enc_flag base64 -d step1 base64 -d step2 base64 -d step3 base64 -d step4`

Hasta que finalmente el resultado dejó de tener estructura Base64 y apareció el formato:

`picoCTF{...}`


Indicadores de múltiples capas Base64

Se puede sospechar múltiples capas cuando:

- El resultado sigue teniendo:
    
    - Caracteres válidos de Base64
        
    - Terminación en `=` o `==`
        
- No aparecen caracteres especiales ni texto legible
    

Durante el reto se aplicaron:

- Navegación en Linux
    
- Uso de `wget` para descargar archivos
    
- Uso de `cat` para visualizar contenido
    
- Uso de `base64 -d` para decodificación
    
- Identificación de patrones de codificación

## Referencias
- Josefsson, S. (2006). _The Base16, Base32, and Base64 Data Encodings_. RFC 4648.  
    [https://datatracker.ietf.org/doc/html/rfc4648](https://datatracker.ietf.org/doc/html/rfc4648)
    
- GNU Project. (2023). _base64 - GNU coreutils manual_.  
    [https://www.gnu.org/software/coreutils/manual/html_node/base64-invocation.html](https://www.gnu.org/software/coreutils/manual/html_node/base64-invocation.html)
    
- picoCTF. (2024). _picoCTF Practice Challenges_.  
    [https://picoctf.org/](https://picoctf.org/)
    
- Stallings, W. (2017). _Cryptography and Network Security: Principles and Practice_. Pearson.