## vault-door-4
## Descripcion
This vault uses ASCII encoding for the password.The source code for this vault is here: [VaultDoor4.java](https://challenge-files.picoctf.net/c_fickle_tempest/92aa3358fb5bde2c6f38b39fbf2d59af8c44220bc0662ce636d655f0ad3a1a8d/VaultDoor4.java)
## Solucion

- Examinamos el código fuente en Java que se nos da
- La Flag esta codificada en diferentes sistemas numericos solo hay que convertirlos a texto
### Forma 1 - javascript
- Ejecutamos el siguiente código en una consola javascript del navegador
```java
String.fromCharCode(106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  , 0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,0142, 0131, 0164, 063 , 0163, 0137, 0143, 061)  + ['9' , '4' , 'f' , '7' , '4' , '5' , '8' , 'e'].join('')
```
###  Forma 2 - modificando código en JAva
- Modificamos el código fuente en Java para hacerlo
```java
import java.util.*;

class VaultDoor4 {
    public static void main(String args[]) {
        VaultDoor4 vaultDoor = new VaultDoor4();
        //Scanner scanner = new Scanner(System.in);
        //System.out.print("Enter vault password: ");
        //String userInput = scanner.next();
    //String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
    if (vaultDoor.checkPassword()) {
        System.out.println("Access granted.");
    } else {
        System.out.println("Access denied!");
        }
    }

    // -Minion #7781
    public boolean checkPassword() {
        //byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0143, 061 ,
            '9' , '4' , 'f' , '7' , '4' , '5' , '8' , 'e' ,
        };
    /*     for (int i=0; i<32; i++) {
            if (passBytes[i] != myBytes[i]) {
                return false;
            }
        } */
        String flag = new String(myBytes);
        System.out.println(flag);
        return true;
    }
}
```
**picoCTF{jU5t_4_bUnCh_0f_bYt3s_b4e943c3a0}**
## Notas
#### El truco de las bases numéricas

El código divide la contraseña en 4 bloques de 8 caracteres. Cada bloque está escrito en una base o formato diferente, pero todos se pueden traducir directamente a texto (caracteres ASCII):

**1. Base Decimal (Índices 0 al 7):** Son números enteros comunes y corrientes. Si buscamos sus equivalentes en texto:

- `106, 85, 53, 116, 95, 52, 95, 98` se traduce a: **`jU5t_4_b`**
    

**2. Base Hexadecimal (Índices 8 al 15):** En Java, el prefijo `0x` indica que el número es hexadecimal.

- `0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f` se traduce a: **`UnCh_0f_`**
    

**3. Base Octal (Índices 16 al 23):** Aquí está la trampa más común: en Java, si un número empieza con un `0` (cero), el compilador lo lee como octal (base 8).

- `0142, 0131, 0164, 063, 0163, 0137, 0142, 064` se traduce a: **`bYt3s_b4`**
    

**4. Caracteres literales (Índices 24 al 31):** Al final, el minion se rindió y simplemente escribió las letras tal cual entre comillas simples.

- `'e' , '9' , '4' , '3' , 'c' , '3' , 'a' , '0'` se traduce a: **`e943c3a0`**
## Referencias
