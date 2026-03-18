## WebNet0
## Descripcion
We found this [packet capture](https://challenge-files.picoctf.net/c_fickle_tempest/66113619363fca174ef6bf56587007af1626f99c44fc5cf92333f9fd8876ce9a/capture.pcap) and [key](https://challenge-files.picoctf.net/c_fickle_tempest/66113619363fca174ef6bf56587007af1626f99c44fc5cf92333f9fd8876ce9a/picopico.key). Recover the flag.
## Solucion

## WebNet0
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
-  Ve a Edit - Preferences - Protocols - TLS 
   - ponemos la llave en RSA Keys list en la columna de key
   - ponemos un nombre a TLS debug file
- Ve a Edit - Find Next , Packet Details (en el primer drop down list), `String` picoCTF
- En el encapsulado, seleccionar la bander - click botón derecho copy .. as pritable text
### Forma 2 
- Decodificar el paquete usando la llave rsa con `ssldump`:
```
ssldump -r capture.pcap -k picopico.key -d | grep pico -A 2
```
**picoCTF{nongshim.shrimp.crackers}**
## Notas
**Transport Layer Security** (**TLS**) is a [cryptographic protocol](https://en.wikipedia.org/wiki/Cryptographic_protocol "Cryptographic protocol") designed to provide communications security over a [computer network](https://en.wikipedia.org/wiki/Computer_network "Computer network"), such as the [Internet](https://en.wikipedia.org/wiki/Internet "Internet"). The [protocol](https://en.wikipedia.org/wiki/Communication_protocol "Communication protocol") is widely used in [applications](https://en.wikipedia.org/wiki/Application_software "Application software") such as [email](https://en.wikipedia.org/wiki/Email "Email"), [instant messaging](https://en.wikipedia.org/wiki/Instant_messaging "Instant messaging"), and [voice over IP](https://en.wikipedia.org/wiki/Voice_over_IP "Voice over IP"), but its use in securing [HTTPS](https://en.wikipedia.org/wiki/HTTPS "HTTPS") remains the most publicly visible.

The TLS protocol aims primarily to provide security, including [privacy](https://en.wikipedia.org/wiki/Privacy "Privacy") (confidentiality), integrity, and authenticity through the use of [cryptography](https://en.wikipedia.org/wiki/Cryptography "Cryptography"), such as the use of [certificates](https://en.wikipedia.org/wiki/Public_key_certificate "Public key certificate"), between two or more communicating computer applications. It runs in the [presentation layer](https://en.wikipedia.org/wiki/Presentation_layer "Presentation layer") and is itself composed of two layers: the TLS record and the TLS [handshake protocols](https://en.wikipedia.org/wiki/Handshake_\(computing\) "Handshake (computing)").
## Referencias

TLS > [https://en.wikipedia.org/wiki/Transport_Layer_Security](https://en.wikipedia.org/wiki/Transport_Layer_Security "https://en.wikipedia.org/wiki/Transport_Layer_Security")