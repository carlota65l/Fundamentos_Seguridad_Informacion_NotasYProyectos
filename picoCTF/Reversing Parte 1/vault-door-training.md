## vault-door-training
## Descripcion
Your mission is to enter Dr. Evil's laboratory and retrieve the blueprints for his Doomsday Project. The laboratory is protected by a series of locked vault doors. Each door is controlled by a computer and requires a password to open. Unfortunately, our undercover agents have not been able to obtain the secret passwords for the vault doors, but one of our junior agents obtained the source code for each vault's computer! You will need to read the source code for each level to figure out what the password is for that vault door. As a warmup, we have created a replica vault in our training facility.The source code for the training vault is here: [VaultDoorTraining.java](https://challenge-files.picoctf.net/c_fickle_tempest/379ca32f89b74c70403ef5b6515ae2f1d2405e66735347b70bc2ef8063084688/VaultDoorTraining.java)
## Solucion
- **El formato de entrada:** En la función `main`, vemos la línea `String input = userInput.substring("picoCTF{".length(),userInput.length()-1);`. Esto nos indica que el programa espera que tu contraseña comience con `picoCTF{` y termine con `}`.
    
- **La contraseña _hardcodeada_:** En la función `checkPassword` (junto a los comentarios del Minion #9567), vemos exactamente el texto que el programa está validando: `return password.equals("w4rm1ng_Up_w1tH_jAv4_000wYdiGTvt");`.

**picoCTF{w4rm1ng_Up_w1tH_jAv4_000wYdiGTvt}**
## Notas
#### La vulnerabilidad: Hardcoding de Credenciales

El concepto central de este ejercicio es el **hardcoding** (código rígido o embebido). Ocurre cuando un programador escribe contraseñas, tokens de acceso o claves de API directamente como texto plano en el código fuente de una aplicación.

- **El problema en el mundo real:** Si un atacante consigue el código fuente (por un repositorio público de GitHub mal configurado, un empleado descontento, o ingeniería inversa), el sistema queda comprometido instantáneamente.
    
- **Referencia estándar:** En la industria de la ciberseguridad, esta vulnerabilidad está clasificada y documentada bajo el estándar **CWE-798: Use of Hard-coded Credentials**.
    

#### Análisis Estático (Static Analysis)

Lo que acabas de hacer es un análisis estático básico. Es la técnica de revisar el código de un programa sin llegar a ejecutarlo (en contraposición al análisis dinámico, que es observar cómo se comporta mientras corre). Leer los comentarios dejados por el "Minion #9567" es parte de buscar pistas, algo muy común en el _pentesting_ y los CTFs.
## Referencias
Ingeniería Inversa (Reverse Engineering)
