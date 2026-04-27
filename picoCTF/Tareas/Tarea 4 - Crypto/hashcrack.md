## hashcrack
## Descripcion
A company stored a secret message on a server which got breached due to the admin using weakly hashed passwords. Can you gain access to the secret stored within the server?Access the server using `nc verbal-sleep.picoctf.net 55355`
## Solucion
**picoCTF{UseStr0nG_h@shEs_&PaSswDs!_4de57566}**
## Notas
- **Hashes vs. Encriptación:** Un _hash_ (como MD5 o SHA-256) es una función matemática unidireccional. A diferencia de la encriptación tradicional, **un hash no se puede "desencriptar"** con una llave. La única forma de descubrir la contraseña original es mediante colisiones o comparaciones (calcular el hash de miles de palabras hasta que el resultado coincida exactamente con el hash robado).
    
- **La vulnerabilidad del Administrador (Falta de "Salting"):** El ejercicio menciona explícitamente "weakly hashed passwords". Esto significa que el administrador usó un algoritmo rápido y obsoleto (como MD5) y no utilizó _Salting_. La "sal" es una cadena de texto aleatoria que se añade a cada contraseña antes de aplicar el hash. Sin salting, una contraseña débil como `123456` siempre generará el mismo hash, permitiendo que cualquiera lo busque y lo rompa instantáneamente.
    
- **El legendario `rockyou.txt`:** Es el diccionario por excelencia en ciberseguridad y CTFs (Capture The Flag). Proviene de una brecha de datos real en 2009 a la empresa _RockYou_, donde se filtraron 32 millones de contraseñas en texto plano. Si un reto implica romper contraseñas, tu primera prueba siempre debe ser contra esta lista.
## Referencias
- **CrackStation:** [crackstation.net](https://crackstation.net) La referencia online más rápida. Utiliza _Rainbow Tables_ (tablas gigantescas con miles de millones de hashes ya precomputados) para encontrar coincidencias de forma casi inmediata, ideal para retos básicos.
    
- **Hashcat:** [hashcat.net](https://hashcat.net/hashcat/) Es la herramienta más rápida y avanzada del mundo para romper hashes de manera local. Utiliza la potencia de tu tarjeta gráfica (GPU) para realizar ataques de fuerza bruta masivos. _Comando de referencia para MD5:_ `$ hashcat -m 0 hash_del_admin.txt /ruta/a/rockyou.txt`