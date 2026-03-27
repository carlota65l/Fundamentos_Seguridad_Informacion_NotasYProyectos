## ### Java Code Analysis!?!

## Descripcion
BookShelf Pico, my premium online book-reading service.I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book!Here are the credentials to get you started:

- Username: "user"
- Password: "user"

Source code can be downloaded [here](https://artifacts.picoctf.net/c/484/bookshelf-pico.zip).Website can be accessed [here!](http://saturn.picoctf.net:52997/).
## Solucion
Al analizar el código fuente proporcionado, específicamente en el archivo `io/github/nandandesai/pico/security/SecretGenerator.java`, se identificó una falla en la lógica de generación de claves. Cuando el sistema no encuentra el archivo `server_secret.txt`, invoca el método `generateRandomString(32)` para crear un nuevo secreto. Sin embargo, este método está implementado de forma insegura:

Java

```
private String generateRandomString(int len) {
    // not so random
    return "1234";
}
```

Como resultado, todos los tokens JWT emitidos por el servidor están firmados con la clave HMAC-SHA256 `"1234"`.

- **CWE Asociadas:** * **CWE-798:** Use of Hard-coded Credentials (Uso de credenciales integradas en el código).
    
    - **CWE-330:** Use of Insufficiently Random Values (Uso de valores insuficientemente aleatorios).

**picoCTF{w34k_jwt_n0t_g00d_6e5d7df5}**
## Notas
- **Generación Segura de Entropía:** Reemplazar el método `generateRandomString` por un Generador de Números Pseudoaleatorios Criptográficamente Seguro (CSPRNG), como `java.security.SecureRandom`.
    
- **Longitud y Fuerza de la Clave:** Para el algoritmo HS256, la clave secreta debe tener al menos 256 bits (32 bytes) de entropía real.
    
- **Gestión de Secretos:** Nunca codificar (hardcode) secretos en el código fuente. Las claves deben inyectarse en tiempo de ejecución a través de variables de entorno o mediante un gestor de secretos (como HashiCorp Vault, AWS Secrets Manager, etc.)
## Referencias
- **RFC 7519 - JSON Web Token (JWT):** [https://datatracker.ietf.org/doc/html/rfc7519](https://datatracker.ietf.org/doc/html/rfc7519)
    
- **OWASP Top 10 - A01:2021-Broken Access Control:** [https://owasp.org/Top10/es/A01_2021-Broken_Access_Control/](https://owasp.org/Top10/es/A01_2021-Broken_Access_Control/)
    
- **OWASP Top 10 - A02:2021-Cryptographic Failures:** [https://owasp.org/Top10/es/A02_2021-Cryptographic_Failures/](https://owasp.org/Top10/es/A02_2021-Cryptographic_Failures/)
    
- **JWT Security Cheat Sheet (OWASP):** [https://cheatsheetseries.owasp.org/cheatsheets/JSON_Web_Token_for_Java_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/JSON_Web_Token_for_Java_Cheat_Sheet.html)