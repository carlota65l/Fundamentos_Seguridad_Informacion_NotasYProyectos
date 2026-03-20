## Piece by Piece
## Descripcion
After logging in, you will find multiple file parts in your home directory. These parts need to be combined and extracted to reveal the flag.SSH to `dolphin-cove.picoctf.net`:`65200` and login as `ctf-player` with password `6abf4a82`.
## Solucion
1. **Explorar** el directorio home → se encuentran fragmentos `part_aa` a `part_ae`
2. **Combinar** los fragmentos (divididos con `split`):

```bash
   cat part_aa part_ab part_ac part_ad part_ae > combined_file
```

3. **Identificar** el tipo de archivo:

```bash
   file combined_file   # → Zip archive data
```

4. **Extraer** el ZIP con contraseña:

```bash
   unzip -P supersecret combined_file
```

5. **Leer** la flag:

```bash
   cat flag.txt
```

**Flag:** **picoCTF{z1p_and_spl1t_f1l3s_4r3_fun_2d6c5d3f}**

## Notas
|Comando|Uso|
|---|---|
|`split`|Divide un archivo en partes (genera sufijos `aa`, `ab`...)|
|`cat part_* > file`|Recombina los fragmentos en orden|
|`file <archivo>`|Identifica el tipo de archivo por sus magic bytes|
|`unzip -P <pass>`|Extrae un ZIP con contraseña sin prompt interactivo|
## Referencias
- [picoCTF Platform](https://picoctf.org)
- `man split` / `man unzip` – manuales de Linux
- [Linux `file` command – magic bytes](https://linux.die.net/man/1/file)