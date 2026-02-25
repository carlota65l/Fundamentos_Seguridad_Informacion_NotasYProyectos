## Scavenger Hunt

## Descripcion

There is some interesting information hidden around this site. Can you find it?
http://wily-courier.picoctf.net:53083/.DS_Store
## Solucion


### solucion 


<!-- Here's the first part of the flag: picoCTF{t -->
/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */

User-agent: *
Disallow: /index.html
Part 3: t_0f_pl4c
I think this is an apache server... can you Access the next flag?

Part 4: 3s_2_lO0k

Congrats! You've completed the scavenger hunt! Part 5: _9588550}


Respuesta: **picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_9588550}**
## Notas

la flag está escondida en varios lugares:

- HTML → comentario
    
- CSS → comentario
    
- robots.txt → archivo oculto
    
- Archivos del servidor
    
- Headers o rutas ocultas
    

La idea es inspeccionar todo el sitio, no solo la página visible.
## Referencias

- Usar el inspector en el navegador
    - Acceder a htm
    - Acceder a hoja de estilos
- Acceder a robots.txt
- Acceder al .htaccess Apache Server : https://httpd.apache.org/docs/2.4/en/howto/htaccess.html
- Acceder al .DS_Store mac file: https://en.wikipedia.org/wiki/.DS_Store