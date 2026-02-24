## picobrowser
## Descripcion

This website can be rendered only by picobrowser, go and catch the flag!http://fickle-tempest.picoctf.net:52619
## Solucion


### solucion 1_ Headers



✅ **Bandera completa:**

belovedcis@DESKTOP-LNGE826:~$ curl -s http://fickle-tempest.picoctf.net:52619/flag -H 'User_agent: picobrowser' | grep pico
         <!-- <strong>Title</strong> --> picobrowser!
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{p1c0_s3cr3t_ag3nt_fba5c48f}</code></p>
            
## Notas



1. Identificar valor de `split`
    
2. Calcular rangos
    
3. Ordenar bloques por posición
    
4. Concatenar
    

### Conceptos clave

- Indexación de strings
    
- Reconstrucción por bloques
    
- Análisis lógico
## Referencias


- nstalar extension de navegador: User-Agent Switcher and Manager
- Obtener con el comando curl:

`curl https://jupiter.challenges.picoctf.org/problem/28921/flag -H "User-Agent:picobrowser" | grep pico`