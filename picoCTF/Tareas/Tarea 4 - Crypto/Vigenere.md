## Vigenere
## Descripcion
Can you decrypt this message?Decrypt this [message](https://artifacts.picoctf.net/c/158/cipher.txt) using this key "CYLAB".
## Solucion

**picoCTF{D0NT_US3_V1G3N3R3_C1PH3R_ae82272q}**
## Notas
The **Vigenère cipher** (French pronunciation: [[viʒnɛːʁ]](https://en.wikipedia.org/wiki/Help:IPA/French "Help:IPA/French")) is a method of [encrypting](https://en.wikipedia.org/wiki/Encryption "Encryption") alphabetic text where each letter of the [plaintext](https://en.wikipedia.org/wiki/Plaintext "Plaintext") is encoded with a different [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher "Caesar cipher"), whose increment is determined by the corresponding letter of another text, the [key](https://en.wikipedia.org/wiki/Key_\(cryptography\) "Key (cryptography)"). In a [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher "Caesar cipher"), each letter of the alphabet is shifted along some number of places. In a Caesar cipher of shift 3, `a` would become `D`, `b` would become `E`, `y` would become `B` and so on. The Vigenère cipher has several Caesar ciphers in sequence with different shift values.

For example, if the plaintext is `attacking tonight` and the key is `oculorhinolaryngology`, then

- the first letter of the plaintext, `a`, is shifted by 14 positions in the alphabet (because the first letter of the key, `o`, is the 14th letter of the alphabet, counting from zero), yielding `o`;

- the second letter, `t`, is shifted by 2 (because the second letter of the key, `c`, is the 2nd letter of the alphabet, counting from zero) yielding `v`;

- the third letter, `t`, is shifted by 20 (`u`), yielding `n`, with wrap-around;

and so on.

Traditionally spaces and punctuation are removed prior to encryption[[1]](https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher#cite_note-1) and reintroduced afterwards.

- In this example the tenth letter of the plaintext `t` is shifted by 14 positions (because the tenth letter of the key `o` is the 14th letter of the alphabet, counting from zero). Therefore, the encryption yields the message `ovnlqbpvt hznzeuz`.
## Referencias
https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher

https://gchq.github.io/CyberChef/#recipe=Vigen%C3%A8re_Decode('CYLAB')&input=cmdub0RWRHtPME5VX1dRM19HMUczTzNUM19BMUFIM1NfY2M4MjI3MmJ9DQo&ieol=CRLF&oeol=CRLF
