## Ph4nt0m 1ntrud3r
## Descripcion

A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/4d25aca04e2409ba0d917d8ed27d49c6fb616ff9603fa3926712cce623a3d7f5/myNetworkTraffic.pcap) and try to get the flag.
## Solucion
- **Reconocimiento Inicial:** Al analizar la jerarquía de protocolos con `tshark`, se determinó que la captura contenía únicamente tráfico TCP dirigido al puerto 80. No había canales encubiertos comunes como ICMP (Ping) o consultas DNS anómalas.
    
- **Identificación de la Anomalía:** Se observó que todos los paquetes TCP enviados por el atacante tenían el **Número de Secuencia alterado (Seq=0)**. Esto es un comportamiento malicioso diseñado para confundir a los analizadores de red (como Wireshark), provocando que los paquetes se registren como simples "Retransmisiones TCP" y evitando que la opción estándar de "Seguir Flujo TCP" (Follow TCP Stream) pudiera reensamblar el mensaje.
    
- **Análisis de la Pista ("Timely manner"):** Como los paquetes tenían el mismo número de secuencia y estaban desordenados dentro de la captura, la única métrica confiable para rearmar el rompecabezas era el tiempo de llegada exacto de cada paquete (Timestamp cronológico).
    
- **Extracción y Decodificación (Scripting):** Se desarrolló un script en Python que automatizó los siguientes pasos:
    
    - Usar `tshark` para extraer la estampa de tiempo (`frame.time_epoch`) y la carga útil en hexadecimal (`tcp.payload`) de cada paquete.
        
    - Ordenar los fragmentos de datos estrictamente por su estampa de tiempo.
        
    - Convertir el texto hexadecimal a caracteres ASCII legibles, lo que reveló múltiples cadenas codificadas en Base64.
        
    - Decodificar las cadenas Base64 en orden, ensamblando finalmente el mensaje oculto y revelando la flag.

**picoCTF{1t_w4snt_th4t_34sy_tbh_4r_8e10e839}**

## Notas

- **Manipulación de Números de Secuencia (TCP Sequence Spoofing):** En una conexión TCP legítima, los números de secuencia aumentan para mantener el orden de los datos. En este ataque, forzar un `Seq=0` constante sirvió como mecanismo de ofuscación (Evasión de IDS/Analizadores) para ocultar el payload fragmentado bajo la apariencia de simples errores de red o retransmisiones.
    
- **Canales Encubiertos basados en el Tiempo y Orden:** Aunque no era un "timing channel" puro (donde el tiempo representa la letra), el tiempo de llegada (`epoch time`) fue el único vector de reensamblaje válido, validando la pista del reto.
    
- **Análisis de Carga Útil en Crudo (Raw Payload Analysis):** Cuando las herramientas de alto nivel de Wireshark fallan por la manipulación del protocolo, el analista debe descender a la capa de bytes y extraer el payload manualmente de los paquetes individuales.
## Referencias

- **Sobre el funcionamiento del Protocolo TCP y Números de Secuencia:** Postel, J. (1981). _Transmission Control Protocol (RFC 793)_. Internet Engineering Task Force (IETF). Recuperado de: [https://datatracker.ietf.org/doc/html/rfc793](https://datatracker.ietf.org/doc/html/rfc793)
    
- **Sobre la extracción avanzada con TShark:** Wireshark Foundation. (s.f.). _tshark(1) Manual Page_. Recuperado de: [https://www.wireshark.org/docs/man-pages/tshark.html](https://www.wireshark.org/docs/man-pages/tshark.html) _(Especialmente la sección sobre la extracción de campos `-T fields`)_.