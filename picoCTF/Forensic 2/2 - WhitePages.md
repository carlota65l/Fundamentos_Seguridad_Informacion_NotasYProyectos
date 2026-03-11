## WhitePages
## Descripcion
I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://challenge-files.picoctf.net/c_fickle_tempest/4de4b105d28cb6df34d9805217f2460b978a37dafc3dfc50edadd8d424dd311a/whitepages.txt) is all blank!
## Solucion

### solucion 1_ usando python

picoCTF{not_all_spaces_are_created_equal_f5d46aff52c6e17f9fd6317b33d2d783}
## Notas
#### Unicode: El "Diccionario Universal"

Unicode es un estándar internacional que le asigna un número único (llamado **Code Point**) a cada carácter que existe en el mundo. No importa si es una letra latina, un kanji japonés, un jeroglífico o el emoji de un taco; todos tienen su lugar en la lista de Unicode.

- **El problema que resolvió:** Antes, cada país tenía su propio sistema. Si enviabas un archivo de Rusia a México, los caracteres se "rompían" y veías símbolos extraños (el famoso _Mojibake_).
    
- **Capacidad:** Tiene espacio para más de 1.1 millones de caracteres.
## Referencias
https://gchq.github.io/CyberChef/