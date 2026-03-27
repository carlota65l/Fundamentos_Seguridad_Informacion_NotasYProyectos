## Glory of the Garden

## Descripcion
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz).
## Solucion
El objetivo del ejercicio es corregir un error en un programa escrito en Rust relacionado con el uso de funciones **inseguras (unsafe)**, para permitir su ejecución correcta y obtener la flag.

A diferencia de los retos anteriores:

- _fixme1_ → errores de sintaxis
- _fixme2_ → errores de borrowing
- _fixme3_ → uso de **unsafe Rust**

picoCTF{n0w_y0uv3_f1x3d_1h3m_411}

## Notas

##### Seguridad de memoria

El uso de `unsafe`:

- Da control total al programador
- Elimina ciertas protecciones del compilador
- Debe usarse con precaución
## Referencias
- Rust Project  
    _The Rust Programming Language – Unsafe Rust_  
    [https://doc.rust-lang.org/book/ch19-01-unsafe-rust.html](https://doc.rust-lang.org/book/ch19-01-unsafe-rust.html)
- Cargo Documentation  
    [https://doc.rust-lang.org/cargo/](https://doc.rust-lang.org/cargo/)
- std::slice::from_raw_parts  
    Documentación oficial  
    [https://doc.rust-lang.org/std/slice/fn.from_raw_parts.html](https://doc.rust-lang.org/std/slice/fn.from_raw_parts.html)
- PicoCTF  
    _General Skills – Rust fixme3 Challenge_