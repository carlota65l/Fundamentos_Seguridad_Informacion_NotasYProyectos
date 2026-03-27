## flag_shop

## Descripcion
There's a flag shop selling stuff, can you buy a flag?[Source](https://challenge-files.picoctf.net/c_fickle_tempest/3b8dcb92959510cff4c72e182cec42febd0b32bd1911c385e3a4a74a03181e9d/store.c). Connect with nc fickle-tempest.picoctf.net 64797.
## Solucion

**picoCTF{m0n3y_bag5_F2Eb382F}**

## Notas
**Concepto Principal:** Un **Integer Overflow** (o desbordamiento de entero) ocurre cuando el resultado de una operación aritmética (como una suma o multiplicación) excede el valor máximo que el tipo de dato de destino puede almacenar en la memoria.

## Referencias
- **CWE-190: Integer Overflow or Wraparound**
    
    - **Descripción:** Es la base de datos oficial del _Common Weakness Enumeration_ (CWE) del MITRE que cataloga este tipo de vulnerabilidad de software.
        
    - **Búsqueda recomendada:** "MITRE CWE-190"
        
- **OWASP - Integer Overflow**
    
    - **Descripción:** La fundación OWASP tiene guías excelentes sobre cómo los desbordamientos pueden llevar a problemas de seguridad graves (como saltarse validaciones de seguridad o ejecutar código).
        
    - **Búsqueda recomendada:** "OWASP Integer Overflow"
        
- **Aritmética de Complemento a dos (Two's Complement)**
    
    - **Descripción:** Aprender esto es fundamental para entender el hacking de memoria y el reversing. Te enseñará cómo la CPU suma, resta y entiende el signo de los números binarios.
        
    - **Búsqueda recomendada:** "Two's complement binary representation"
        
- **Prevención (Safe Math / SafeInt)**
    
    - **Descripción:** Para evitar esto, los programadores modernos usan librerías que validan las multiplicaciones antes de hacerlas (ej. `SafeMath` en Solidity para criptomonedas, o chequeos del compilador en Rust/C++).