## shark on wire 2
## Descripcion
We found this [packet capture](https://challenge-files.picoctf.net/c_fickle_tempest/d2051a169bcab758191e43355c6954ae40a96b0791d75ad33737c7e9ca42703b/capture.pcap). Recover the flag.
## Solucion
- Verificamos el archivo, vemos que es un archivo `.pcap` de captura de paquetes

`wireshark capture.pcap &`  

- Establecemos un filtro en el stream 32 y 60 y vemos marcas de `begin` y `end`

`udp.stream eq 32 udp.stream eq 60`

- Ahora observamos que el puerto destino udp es 22, establecemos fitro

`udp.dstport == 22`

- El puerto origen, si le quitas - 5000, iba formando las caracteres ascii en decimal y obtienes la flag

`>>> chr(112) 'p' >>> chr(105) 'i' >>> chr(99) 'c' >>> chr(111) 'o' >>>` 

- Otra forma es con `scapy` en python, primero instalamos `scapy`

`sudo apt install python3-scapy` 

- luego programamos el exploit que nos de la flag

````
`from scapy.all import *  packets = rdpcap('capture.pcap')  
flag=''  for p in packets:     
if UDP in p and p[UDP].dport == 22:         i
f p[UDP].sport > 5000:             f
lag+=chr(p[UDP].sport - 5000)  
print(flag)`
````

picoCTF{p1LLf3r3d_data_v1a_st3g0}
## Notas
Wireshark es la herramienta estándar para el análisis de tráfico de red. En este reto, su uso es para **identificar patrones**.

- **Streams (Flujos):** Un `udp.stream` agrupa todos los paquetes que pertenecen a una misma conversación entre dos IPs y puertos. Identificar los streams 32 y 60 con marcas de `begin` y `end` indica que el "mensaje" está contenido entre esos dos puntos temporales.
    
- **Filtros de Visualización:**
    
    - `udp.dstport == 22`: Filtra el tráfico cuyo puerto de destino es el 22. Aunque el puerto 22 suele ser SSH (TCP), aquí se usa sobre UDP como un **indicador o "faro" (beacon)** para separar el tráfico de la flag del resto del ruido de la captura.
        
- **Análisis de Campos No Convencionales:** La clave del reto es notar que el `udp.sport` (puerto de origen) varía constantemente. En un tráfico normal, el puerto de origen no suele llevar información codificada.
- 
Cuando una captura tiene cientos o miles de paquetes, hacerlo a mano con `chr()` en Python es inviable. Scapy es la librería de manipulación de paquetes más potente para Python.

- **`rdpcap('archivo.pcap')`**: Lee la captura completa y la carga en una lista de objetos de paquetes en memoria.
    
- **Capas (Layers):** Scapy organiza los paquetes por capas. `if UDP in p` verifica si el paquete tiene la capa de protocolo UDP.
    
- **Atributos de Clase:** `p[UDP].sport` accede directamente al valor numérico del puerto de origen.
    
- **Lógica del Desplazamiento (Offset):** El uso de `- 5000` es un método de ofuscación simple. Los puertos válidos van del 1 al 65535. Al sumar 5000 a un valor ASCII (como el de 'p' que es 112), el resultado es 5112, un número de puerto perfectamente válido que no levanta sospechas inmediatas.
## Referencias

- **Código ASCII:** Es la referencia base. Los caracteres imprimibles suelen estar en el rango decimal 32-126. Si al analizar puertos ves números en un rango constante (como 5032-5126), es una señal clara de un desplazamiento ASCII.
    
- **Covert Channels (Canales Encubiertos):** Este reto se basa en el principio de utilizar campos de cabecera de red para fines distintos a los que fueron diseñados. Se pueden ocultar datos en:
    
    - Números de secuencia TCP.
        
    - Campos ID de IP.
        
    - Puertos de origen/destino (como en este caso).
        
    - Campos de "Checksum" modificados deliberadamente.
        
- **PCAP (Packet Capture):** Es el formato de archivo estándar. Una referencia útil es saber que si `file` te dice que es un _pcap_, siempre puedes intentar extraer archivos ocultos dentro de los paquetes con herramientas como `foremost` o `networkminer`.