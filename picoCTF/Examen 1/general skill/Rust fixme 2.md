## Rust fixme 2

## Descripcion
The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz).
## Solucion
El ejercicio consiste en corregir errores en un programa escrito en Rust relacionados con el manejo de **referencias y mutabilidad (borrowing)**, para permitir que el programa modifique una cadena y muestre la flag.

A diferencia del reto anterior (_fixme1_), aquí:

- No hay errores de sintaxis básicos
- El problema está en el **sistema de ownership y borrowing**

**picoCTF{4r3_y0u_h4v1n5_fun_y31?}**
## Notas

- Sistema de **ownership** en Rust
- Referencias:
    - `&T` → inmutable
    - `&mut T` → mutable
- Seguridad de memoria sin garbage collector
- Prevención de errores como:
    - data races
    - modificaciones no controladas
## Referencias
- Rust Project  
    _The Rust Programming Language – References and Borrowing_  
    [https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html](https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html)
- Cargo Documentation  
    [https://doc.rust-lang.org/cargo/](https://doc.rust-lang.org/cargo/)
- Rust Compiler  
    Documentación oficial del compilador  
    [https://doc.rust-lang.org/rustc/](https://doc.rust-lang.org/rustc/)
- PicoCTF  
    _General Skills – Rust fixme2 Challenge_