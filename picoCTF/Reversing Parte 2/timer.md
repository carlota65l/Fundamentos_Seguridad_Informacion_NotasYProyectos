## timer
## Descripcion
You will find the flag after analysing this apkDownload [here](https://artifacts.picoctf.net/c/449/timer.apk).
## Solucion
- Instalar `jadx` decompilador de java
```
sudo apt install jadx
```
- Abrir el archivo `.apk` del reto : `File - Open Files`
- Una vez abierto el archivo `Navitation - Text Search` y escribe `picoCTF`
```java
package com.example.timer;

/* JADX INFO: loaded from: classes3.dex */
public final class BuildConfig {
    public static final String APPLICATION_ID = "com.example.timer";
    public static final String BUILD_TYPE = "debug";
    public static final boolean DEBUG = Boolean.parseBoolean("true");
    public static final int VERSION_CODE = 1;
    public static final String VERSION_NAME = "picoCTF{...}";
}
```

**picoCTF{t1m3r_r3v3rs3d_succ355fully_17496}**
## Notas
Si utilizas una herramienta como `jadx` para abrir el archivo `timer.apk` y revisas el archivo `AndroidManifest.xml`, o si simplemente extraes el contenido y utilizas el comando `strings` o buscas la cadena "picoCTF", encontrarás la flag directamente en el código.
## Referencias
https://www.welivesecurity.com/la-es/2023/01/18/herramientas-utiles-analisis-malware-android/