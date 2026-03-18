## Webnet1
## Descripcion
We found this [packet capture](https://challenge-files.picoctf.net/c_fickle_tempest/d1e9add4e31989553f239ebf71ba5972f9bed7bd4932f931e14bfba80d75f815/capture.pcap) and [key](https://challenge-files.picoctf.net/c_fickle_tempest/d1e9add4e31989553f239ebf71ba5972f9bed7bd4932f931e14bfba80d75f815/picopico.key). Recover the flag.
## Solucion

- Verificamos el tipo de archivo, uno es una captura de paquetes, el otro una llave rsa con la que fue encriptado el tráfico TLS en el paquete
```
file capture.pcap
file picopico.key 
```
### Forma 1
- Abrir el archivo con Wireshark
```
wireshark capture.pcap & 
```
- Cambiar la llave rsa , Ve a Edit - Preferences - Protocols - TLS , sigue el mismo procedimiento del reto anterior, solo borra la llave anterior
- Extraer la imagen en el trafico 
  - Ve a File - Export Objects - HTTP
  - Selecciona el archivo `vultre.jpg`
- Click en Save
- Extrae las cadenas en la imagen y encontraras la banera
```
strings -n 10 vulture.jpg 
```
### Forma 2 
- Decodificar el paquete usando la llave rsa con `ssldump`:
```
ssldump -r capture.pcap -k picopico.key -d | grep pi -A 10
```

**picoCTF{honey.roasted.peanuts}**
## Notas

- Si se tiene la clave RSA del servidor:
    
    - Se puede descifrar tráfico TLS capturado
        
- Esto simula un escenario de mala configuración o filtración de claves

Digital Forensics

- Recuperación de evidencia desde tráfico de red
    
- Incluye reconstrucción de archivos y sesiones
## Referencias
- Wireshark Official Documentation
- ssldump Manual
- Transport Layer Security Overview
- Digital Forensics Concepts