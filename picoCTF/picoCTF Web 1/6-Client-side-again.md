## Client-side-again
## Descripcion

Can you break into this super secure portal?http://fickle-tempest.picoctf.net:63610
## Solucion

#### Primero: decodificar el arreglo

El arreglo original es:
var _0x5a46 = [  
"daf93}",  
"_again_4",  
"this",  
"Password Verified",  
"Incorrect password",  
"getElementById",  
"value",  
"substring",  
"picoCTF{",  
"not_this"  
];

Pero luego lo rota:

(function(paths, opt_attributes) {  
  var setter = function(val) {  
    for (;--val;) {  
      paths["push"](paths["shift"]());  
    }  
  };  
  setter(++opt_attributes);  
})(_0x5a46, 435);

Eso significa que el arreglo se mueve muchas veces (435).  
Como 435 % 10 = **5**, el arreglo se rota 5 posiciones.

#### Arreglo después de rotar 5 posiciones

Después de rotarlo 5 veces queda:

[  
"getElementById",   // 0  
"value",            // 1  
"substring",        // 2  
"picoCTF{",         // 3  
"not_this",         // 4  
"daf93}",           // 5  
"_again_4",         // 6  
"this",             // 7  
"Password Verified", // 8  
"Incorrect password" // 9  
]

---


checkpass.substring(8, 16) == "not_this"

Entonces tenemos:

picoCTF{not_this

Otra condición

checkpass.substring(12, 16) == "_aga"

Eso coincide con:

_again_4

#### Última parte

checkpass.substring(16, 24) == "_again_4"

Y termina con:

daf93}

---

### Bandera completa

Uniendo todo:

picoCTF{not_this_again_4daf93}
## Notas

> **Nunca confiar en el lado del cliente.**

Si la validación:

- Está en HTML
    
- Está en JavaScript
    
- Está en cookies manipulables
    

Entonces puede ser burlada.

La seguridad real debe implementarse del lado del servidor.
## Referencias

- javascript obfuscation - [https://jscrambler.com/code-integrity](https://jscrambler.com/code-integrity "https://jscrambler.com/code-integrity")
- javascript deobfuscation: - [http://jsnice.org/](http://jsnice.org/ "http://jsnice.org/"), [https://beautifier.io/](https://beautifier.io/ "https://beautifier.io/")