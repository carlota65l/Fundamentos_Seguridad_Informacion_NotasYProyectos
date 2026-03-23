## - Milkslap
## Descripcion
🥛http://wily-courier.picoctf.net:61017/
## Solucion

- Entrar al sitio web que propone el reto, que se accede haciendo click sobre el icono en forma de vaso de leche
- Revisar el código fuente, hasta llegar a la hoja de estilos .css, ahí se carga un archivo
- Descargar el archivo con `wget` o botón derecho `Open Image in New Tab` y descargarla de ahí

 
`wget http://mercury.picoctf.net:7585/concat_v.png`

- Aplicar `zsteg` ampliando el buffer de ruby para evitar desbordamientos, la bandera aparece

`sudo gem install zsteg  export RUBY_THREAD_VM_STACK_SIZE=500000000 zsteg concat_v.png`

**picoCTF{imag3_m4n1pul4t10n_sl4p5}**
## Notas

- **Reconocimiento web**: inspección de HTML, CSS y recursos cargados.
- **Archivos ocultos**: recursos referenciados indirectamente.
- **Esteganografía**: ocultamiento de información en imágenes.
- **Análisis forense básico** en archivos multimedia.
- Uso de herramientas automatizadas como `zsteg`.
## Referencias
- zsteg  
    Herramienta para detectar datos ocultos en imágenes PNG/BMP usando análisis de bits.
- wget  
    Utilidad para descargar archivos desde la web mediante terminal.