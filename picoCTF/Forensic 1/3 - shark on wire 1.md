## shark on wire 1
## Descripcion
We found this [packet capture](https://challenge-files.picoctf.net/c_fickle_tempest/134d2a2cf6ec5b7e757effc9b32977af7cc324b8e99a5ddb64737794a14dc18d/capture.pcap). Recover the flag.
## Solucion

### solucion 1
**picoCTF{StaT31355_636f6e6e}**

(kali㉿kali)-[~/sharkonwirel]
└─$ wireshark capture.pcap &

## Notas

- **Shark on Wire 1:** En este reto clásico, la flag suele estar en paquetes **UDP**. Filtra por `udp` en Wireshark y ve revisando los "Data" de los paquetes.
    
- **PcapPoisoning:** A veces hay miles de paquetes y la flag está escondida en uno solo; aquí el comando `strings | grep` es tu mejor amigo.
    
- **Protocolos comunes:**
    
    - **ICMP:** Revisa el campo "Data" de los pings.
        
    - **DNS:** A veces la flag está en las consultas de nombres de dominio.
        

**Consejo:** Si el comando `strings` te da muchos resultados basura, intenta: `strings -n 10 capture.pcap` (esto solo muestra cadenas de al menos 10 caracteres, filtrando el ruido).
## Referencias
