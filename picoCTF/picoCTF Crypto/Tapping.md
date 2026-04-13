##  Tapping
## Descripcion

Theres tapping coming in from the wires.
What's it saying nc fickle-tempest.picoctf.net 50246.
## Solucion
 Conectarse vía terminal usando el comando `nc`.
2. Copiar la secuencia de puntos `.` y guiones `-`.
3. Usar un decodificador Morse (como CyberChef).
4. Envolver el mensaje resultante en el formato `picoCTF{MENSAJE_DECODIFICADO}`.

.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. ...-- ---.. --... ....- ----- --... ---.. -.-. } 
PICOCTF{M0RS3C0D31SFUN3874078C}
## Notas
Netcat (nc): Herramienta para conectarse a puertos de red.

• Código Morse: El mensaje "tapping" indica que la flag está codificada en puntos y guiones.
  
## Referencias
https://gchq.github.io/CyberChef/#recipe=From_Morse_Code('Space','Line%20feed')&input=Li0tLiAuLiAtLi0uIC0tLSAtLi0uIC0gLi4tLiB7IC0tIC0tLS0tIC4tLiAuLi4gLi4uLS0gLS4tLiAtLS0tLSAtLi4gLi4uLS0gLi0tLS0gLi4uIC4uLS4gLi4tIC0uIC4uLi0tIC0tLS4uIC0tLi4uIC4uLi4tIC0tLS0tIC0tLi4uIC0tLS4uIC0uLS4gfSANCg&ieol=CRLF&oeol=CRLF