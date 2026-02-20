## Binary search
## Descripcion

Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/17/challenge.zip)

`ssh -p 65204 ctf-player@atlas.picoctf.net`Using the password `f3b61b38`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
## Solucion
### solucion 1_ usando python

 
```bash
 BelovedCis-picoctf@webshell:~$ ssh -p 65204 ctf-player@atlas.picoctf.net
The authenticity of host '[atlas.picoctf.net]:65204 ([18.217.83.136]:65204)' can't be established.
ED25519 key fingerprint is SHA256:M8hXanE8l/Yzfs8iuxNsuFL4vCzCKEIlM/3hpO13tfQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:65204' (ED25519) to the list of known hosts.
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 53
Higher! Try again.
Enter your guess: 75
Higher! Try again.
Enter your guess: 96
Higher! Try again.
Enter your guess: 886
Higher! Try again.
Enter your guess: 900 
Congratulations! You guessed the correct number: 900
Here's your flag: picoCTF{g00d_gu355_6dcfb67c}
Connection to atlas.picoctf.net closed.
BelovedCis-picoctf@webshell:~$ 
```

Respuesta: picoCTF{g00d_gu355_6dcfb67c}


## Notas
#### Conexión remota mediante SSH

SSH (Secure Shell) es un protocolo que permite acceder de forma segura a sistemas remotos a través de una red insegura.

El comando utilizado es:

ssh -p 65204 ctf-player@atlas.picoctf.net
Componentes:

- `ssh`: comando para iniciar conexión segura
- `-p 65204`: especifica el puerto
- `ctf-player`: nombre de usuario
- `atlas.picoctf.net`: servidor remoto

SSH proporciona:

- confidencialidad mediante cifrado
- autenticación segura
- integridad de los datos
## Referencias
- Binary Search - GeeksforGeeks: [https://www.geeksforgeeks.org/binary-search/](https://www.geeksforgeeks.org/binary-search/)
- Binary Search - Khan Academy: [https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search](https://www.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search)
- Python `bisect` module (búsqueda binaria built-in): [https://docs.python.org/3/library/bisect.html](https://docs.python.org/3/library/bisect.html)
- Conexión SSH en CTFs: [https://ctf101.org/](https://ctf101.org/)