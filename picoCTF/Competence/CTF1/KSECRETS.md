## KSECRETS
## Descripcion
We have a kubernetes cluster setup and flag is in the secrets. You think you can get it?Please wait for a minute for the application to be configured!Kubernetes is running at: green-hill.picoctf.net : 51066You can find your configuration file [here](http://green-hill.picoctf.net:53502/kubeconfig).
## Solucion
El objetivo del reto fue acceder a un clúster de Kubernetes expuesto y recuperar una **flag almacenada dentro de un Secret**.

**picoCTF{ks3cr375_41n7_s4f3_c8480165}**

## Notas
#### ¿Qué es Kubernetes?

Kubernetes es una plataforma de orquestación de contenedores que permite desplegar, escalar y administrar aplicaciones en contenedores.
#### ¿Qué son los Secrets?

Los **Secrets** en Kubernetes son objetos que almacenan información sensible como:

- contraseñas
    
- tokens
    
- claves API
    
- certificados
    

**📌 Importante:**

- Los datos se almacenan en **Base64**, NO en texto plano.
    
- Base64 **no es cifrado**, solo codificación.
## Referencias

- Kubernetes Docs  
    [https://kubernetes.io/docs/](https://kubernetes.io/docs/)
- Kubernetes Secrets  
    [https://kubernetes.io/docs/concepts/configuration/secret/](https://kubernetes.io/docs/concepts/configuration/secret/)
- OWASP Kubernetes Top 10  
    [https://owasp.org/www-project-kubernetes-top-ten/](https://owasp.org/www-project-kubernetes-top-ten/)
- Kubernetes Hardening Guide  
    [https://kubernetes.io/docs/tasks/administer-cluster/securing-a-cluster/](https://kubernetes.io/docs/tasks/administer-cluster/securing-a-cluster/)
- kubectl
- `base64`
- `sed`