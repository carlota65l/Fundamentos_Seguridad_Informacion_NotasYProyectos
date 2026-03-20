## Failure Failure
## Descripcion
Welcome to **Failure Failure** — a high-available system.This challenge simulates a real-world failover scenario where one server is prioritized over the other.A load balancer stands between you and the truth — and it won't hand over the flag until you force its hand.You can begin your journey [here](http://mysterious-sea.picoctf.net:60579/) to try and retrieve the flag.For reference:

- The HAProxy configuration used in this challenge is available [here](https://challenge-files.picoctf.net/c_mysterious_sea/efa02ccac53ec4e51b58cc636d1b90b91eb682db7cfa410aa50f4a340e1f36c4/haproxy.cfg).
- The application code is available [here](https://challenge-files.picoctf.net/c_mysterious_sea/efa02ccac53ec4e51b58cc636d1b90b91eb682db7cfa410aa50f4a340e1f36c4/app.py)
## Solucion

El reto simula un entorno real de alta disponibilidad (High Availability) utilizando un balanceador de carga basado en HAProxy. El objetivo es manipular el comportamiento del sistema para forzar un cambio hacia un servidor de respaldo que contiene la flag.

### Configuración del balanceador

El archivo `haproxy.cfg` define dos servidores:

- **Servidor primario (`s1`)**
    
    - Puerto: 8000
        
    - Atiende tráfico normalmente
        
- **Servidor secundario (`s2`)**
    
    - Puerto: 9000
        
    - Marcado como `backup`
        
    - Solo se usa cuando el primario falla

##### Vulnerabilidad explotada

El sistema confía en que el servidor principal siempre estará disponible.  
Sin embargo, no está protegido contra:

- saturación de peticiones (DoS ligero)
    
- sobrecarga de conexiones concurrentes
Esto permite forzar un **failover manual**

**picoCTF{f41l0v3r_f0r_7h3_w1n_28f14987**
## Notas
### Failover

Mecanismo en sistemas de alta disponibilidad donde:

- un sistema secundario entra en funcionamiento
- cuando el sistema principal falla
###  Load Balancing

Distribución de tráfico entre múltiples servidores para:

- mejorar rendimiento
- aumentar disponibilidad
###  Health Checks

Pruebas automáticas que determinan si un servidor está:

- activo (UP)
- caído (DOWN)
###  Denial of Service (DoS)

Ataque que busca:

- saturar un servicio
- hacerlo inaccesible

En este reto se usa una versión leve para provocar el failover.
## Referencias
- Load balancing  
    https://en.wikipedia.org/wiki/Load_balancing_(computing)
- Failover  
    [https://en.wikipedia.org/wiki/Failover](https://en.wikipedia.org/wiki/Failover)
- Denial-of-service attack  
    [https://en.wikipedia.org/wiki/Denial-of-service_attack](https://en.wikipedia.org/wiki/Denial-of-service_attack)