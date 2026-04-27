##  morse-code
## Descripcion
Morse code is well known. Can you decrypt this?Download the file [here](https://artifacts.picoctf.net/c/79/morse_chal.wav).Wrap your answer with picoCTF{}, put underscores in place of pauses, and use all lowercase.
## Solucion
**picoCTF{wh47_h47h_90d_w20u9h7} ** 

## Notas
The decoder will analyse sound coming from the microphone or from an audio file. The spectrogram of the sound is shown in the main graph along with a pink region showing the frequency being analysed. If the volume in the chosen frequency is louder than the "Volume threshold" then it is treated as being part of a dit or dah, and otherwise it records a gap (this is shown in the lower graph that looks like a barcode). From these timings it determines if something is a dit, dah, or a sort of space and then converts it into a letter shown in the message box.
## Referencias
https://morsecode.world/international/decoder/audio-decoder-adaptive.html