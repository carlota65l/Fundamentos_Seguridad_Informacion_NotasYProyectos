## JaWT Scratchpad
## Descripcion
Check the admin scratchpad!http://fickle-tempest.picoctf.net:53423
## Solucion


picoCTF{jawt_was_just_what_you_thought_bbb82bd4a57564aefb32d69dafb60583}

- Nos logueamos con cualquier usuario
- Copiamos el token jwt a un archivo llamado token
- Lo crackeamos en kali usando john con el diccionario rockyou.txt

`gizip -d /usr/share/wordlists/rockyou.txt.gz john token -w=/usr/share/wordlists/rockyou.txt`

- vamos al sitio jwt debuger, y modificamos el payload por admin
- ponemos la palabra crackeada en la firma
- copiamos el nuevo token generado a la cookie y recargamos la pagina

## Notas

**JSON** (**JavaScript Object Notation**, pronounced [/ˈdʒeɪsən/](https://en.wikipedia.org/wiki/Help:IPA/English "Help:IPA/English") or [/ˈdʒeɪˌsɒn/](https://en.wikipedia.org/wiki/Help:IPA/English "Help:IPA/English")) is an [open standard](https://en.wikipedia.org/wiki/Open_standard "Open standard") file format and [data interchange](https://en.wikipedia.org/wiki/Electronic_data_interchange "Electronic data interchange") format that uses [human-readable](https://en.wikipedia.org/wiki/Human-readable_medium_and_data "Human-readable medium and data") text to store and transmit data objects consisting of [name–value pairs](https://en.wikipedia.org/wiki/Name%E2%80%93value_pair "Name–value pair") and [arrays](https://en.wikipedia.org/wiki/Array_data_type "Array data type") (or other [serializable](https://en.wikipedia.org/wiki/Serialization "Serialization") values). It is a commonly used data format with diverse uses in [electronic data interchange](https://en.wikipedia.org/wiki/Electronic_data_interchange "Electronic data interchange"), including that of [web applications](https://en.wikipedia.org/wiki/Web_application "Web application") with [servers](https://en.wikipedia.org/wiki/Server_\(computing\) "Server (computing)").

JSON is a [programming language-independent](https://en.wikipedia.org/wiki/Language-independent_specification "Language-independent specification") data format. It was derived from [JavaScript](https://en.wikipedia.org/wiki/JavaScript "JavaScript"), but many modern [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language") include code to generate and [parse](https://en.wikipedia.org/wiki/Parse "Parse") JSON-format data. JSON filenames use the extension `.json`.
## Referencias

- JSON: [https://en.wikipedia.org/wiki/JSON](https://en.wikipedia.org/wiki/JSON "https://en.wikipedia.org/wiki/JSON")
- JWT : [https://jwt.io/introduction](https://jwt.io/introduction "https://jwt.io/introduction")
- jwt debugger : [https://jwt.lannysport.net/](https://jwt.lannysport.net/ "https://jwt.lannysport.net/")
- john : [https://github.com/openwall/john](https://github.com/openwall/john "https://github.com/openwall/john")