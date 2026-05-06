## Safe Opener 2
## Descripcion
Can you open this safe?I forgot the key to my safe but this [program](https://artifacts.picoctf.net/c/83/SafeOpener.java) is supposed to help me with retrieving the lost key. Can you help me unlock my safe?Put the password you recover into the picoCTF flag format like:`picoCTF{password}`
## Solucion
Analizando el código fuente de `SafeOpener.java`, el programa le pide al usuario una contraseña, la codifica utilizando Base64 y luego la compara con la siguiente cadena fija:

`cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz`

Para recuperar la llave perdida o contraseña original, solo es necesario decodificar esta cadena de Base64 de vuelta a texto plano. Al decodificar `cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz` obtenemos:

`pl3as3_l3t_m3_1nt0_th3_saf3`

Poniendo la contraseña recuperada en el formato de la flag solicitado, la respuesta final es:

**picoCTF{pl3as3_l3t_m3_1nt0_th3_saf3}**
## Notas
- **Análisis Estático vs. Dinámico:** En este ejercicio utilizamos **Análisis Estático**. Esto significa que encontramos la solución simplemente leyendo el código fuente (`SafeOpener.java`) sin necesidad de compilarlo o ejecutarlo.
    
- **Codificación no es Cifrado (Encoding vs. Encryption):** El programa intenta ocultar la contraseña utilizando **Base64**. Una lección fundamental en ciberseguridad es que _Base64 no es un método de seguridad ni de encriptación_; es un esquema de traducción de datos. Cualquiera que reconozca el formato Base64 puede decodificarlo al instante sin necesitar una clave.
    
- **Credenciales "Hardcodeadas":** El principal fallo de seguridad de la caja fuerte del ejercicio es que el hash/texto codificado (`cGwzYXMzX2wzdF9tM18xbnQwX3RoM19zYWYz`) está escrito directamente en el código fuente. Las contraseñas o secretos nunca deben estar "hardcodeados" en el código de una aplicación.
    
- **Reconocimiento de Patrones:** En el mundo de la ciberseguridad, aprenderás a reconocer Base64 a simple vista. Suele contener letras mayúsculas, minúsculas, números y, muy a menudo, termina con uno o dos signos de igual (`=`) que sirven como relleno (padding).
## Referencias
**CyberChef (La "Navaja Suiza" cibernética):** Es una aplicación web desarrollada por el GCHQ británico. Puedes pegar cadenas de texto y aplicarles "recetas", como por ejemplo la receta _From Base64_. Es indispensable para resolver CTFs.