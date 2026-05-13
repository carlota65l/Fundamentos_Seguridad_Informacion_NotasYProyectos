## asm1
## Descripcion
What does asm1(0x36e) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://challenge-files.picoctf.net/c_fickle_tempest/742701d2dc84a01fe69c48228c14feafdcd3658f83e99b887c550bed0302419e/test.S)

## Solucion
- **Prologue (`<+0>` to `<+5>`)**: The function sets up the stack frame. In 32-bit calling conventions, the first argument passed to the function is located at `[ebp+0x8]`. So, `[ebp+0x8] = 0x36e`.
    
- **First Comparison (`<+7>` to `<+14>`)**:
    
    - `cmp DWORD PTR [ebp+0x8], 0x6c8` compares our argument `0x36e` to `0x6c8`.
        
    - `jg 0x11d6` jumps if our argument is strictly greater. Since `0x36e` (878) is less than `0x6c8` (1736), the jump is **not taken**.
        
- **Second Comparison (`<+16>` to `<+23>`)**:
    
    - `cmp DWORD PTR [ebp+0x8], 0x36e` compares our argument `0x36e` to `0x36e`.
        
    - `jne 0x11ce` jumps if they are not equal. Since they are exactly equal, the jump is **not taken**.
        
- **Execution block (`<+25>` to `<+31>`)**:
    
    - `mov eax, DWORD PTR [ebp+0x8]` moves our argument into the `eax` register. Now, `eax = 0x36e`.
        
    - `add eax, 0x6` adds 6 to `eax`.
        
    - $0x36e + 0x6 = 0x374$. So, `eax = 0x374`.
        
    - `jmp 0x11ed <asm1+64>` jumps to the function epilogue.
        
- **Epilogue (`<+64>` to `<+65>`)**: The function restores the base pointer and returns. The return value is whatever is currently stored in the `eax` register.
**Flag: 0x374**
## Notas
**El Marco de la Pila (Stack Frame)**

- **Prólogo (`<+4>` y `<+5>`):** Las instrucciones `push ebp` y `mov ebp, esp` configuran el marco de la pila. Guardan el estado de la función anterior y establecen a `ebp` (Base Pointer) como el punto de referencia fijo para acceder a las variables locales y argumentos de la función actual.
    
- **Acceso a Argumentos (`[ebp+0x8]`):** En la convención de llamadas estándar de 32 bits (_cdecl_), los argumentos se empujan a la pila antes de llamar a la función.
    
    - `[ebp]` contiene el `ebp` anterior guardado.
        
    - `[ebp+0x4]` contiene la dirección de retorno (a dónde volver cuando acabe la función).
        
    - **`[ebp+0x8]`** contiene el **primer argumento** que se pasó a la función (en tu caso, el valor `0x36e`).
        
- **Epílogo (`<+64>` y `<+65>`):** `pop ebp` desarma el marco de la pila restaurando el estado original, y `ret` saca la dirección de retorno de la pila para regresar el control al programa principal.
## Referencias
Es un problema introductorio excelente diseñado para enseñar a los estudiantes de ciberseguridad e informática cómo leer, seguir el flujo de control y comprender las convenciones de llamadas en código ensamblador x86 de 32 bits.