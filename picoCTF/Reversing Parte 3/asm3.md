## asm3
## Descripcion
What does asm3(0xb58568e8,0xc63ab2a1,0xf9d33ef4) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://challenge-files.picoctf.net/c_fickle_tempest/b3fee52f11c2963c3f6008623c66d7c0906ab439f927132ac7fbc1d53f83c4ee/test.S)
## Solucion

**The Flag`0x9fba`**

### Understanding the Execution

To see exactly how the code arrives at this value, we need to map the arguments onto the 32-bit x86 stack. Because x86 architecture uses **little-endian** byte ordering, the bytes of the arguments are stored in memory in reverse order.

Here is how the three arguments—`0xb58568e8`, `0xc63ab2a1`, and `0xf9d33ef4`—look on the stack relative to the base pointer (`ebp`):

|**Memory Address**|**Byte Value**|**Source**|
|---|---|---|
|`ebp+0x08`|`0xe8`|Argument 1 (`0xb58568e8`)|
|`ebp+0x09`|`0x68`|Argument 1|
|`ebp+0x0a`|`0x85`|Argument 1|
|**`ebp+0x0b`**|**`0xb5`**|Argument 1|
|**`ebp+0x0c`**|**`0xa1`**|Argument 2 (`0xc63ab2a1`)|
|**`ebp+0x0d`**|**`0xb2`**|Argument 2|
|`ebp+0x0e`|`0x3a`|Argument 2|
|`ebp+0x0f`|`0xc6`|Argument 2|
|**`ebp+0x10`**|**`0xf4`**|Argument 3 (`0xf9d33ef4`)|
|**`ebp+0x11`**|**`0x3e`**|Argument 3|
|`ebp+0x12`|`0xd3`|Argument 3|
|`ebp+0x13`|`0xf9`|Argument 3|


## Notas
Let's trace the values inside the `eax` register (and its sub-registers `ax`, `ah`, and `al`) line-by-line:

- `<+7>: xor eax,eax`
    
    Clears the `eax` register completely.
    
    _Current state: `eax = 0x00000000` (`ax = 0x0000`)_
    
- `<+9>: mov ah,BYTE PTR [ebp+0xb]`
    
    Moves the byte at `ebp+0x0b` (`0xb5`) into `ah` (the high 8 bits of `ax`).
    
    _Current state: `ah = 0xb5`, so `ax = 0xb500`_
    
- `<+12>: shl ax,0x10`
    
    Shifts the 16-bit register `ax` left by 16 bits (`0x10`). Because the shift amount matches the size of the register, all bits are pushed completely out, resetting `ax` to zero.
    
    _Current state: `ax = 0x0000`_
    
- `<+16>: sub al,BYTE PTR [ebp+0xd]`
    
    Subtracts the byte at `ebp+0x0d` (`0xb2`) from `al` (`0x00`). In 8-bit unsigned arithmetic, `0x00 - 0xb2 = -178`. Since it wraps around modulo 256, `256 - 178 = 78`, which is `0x4e` in hex.
    
    _Current state: `al = 0x4e`, so `ax = 0x004e`_
    
- `<+19>: add ah,BYTE PTR [ebp+0xc]`
    
    Adds the byte at `ebp+0x0c` (`0xa1`) to `ah` (`0x00`).
    
    _Current state: `ah = 0xa1`, so `ax = 0xa14e`_
    
- `<+22>: xor ax,WORD PTR [ebp+0x10]`
    
    Performs a bitwise XOR between `ax` and the 16-bit WORD starting at `ebp+0x10`. Reading the two little-endian bytes (`0xf4` and `0x3e`), the WORD value is `0x3ef4`.
    
    Calculating `0xa14e ^ 0x3ef4`:
    
    - `0xa` ^ `0x3` = `0x9`
        
    - `0x1` ^ `0xe` = `0xf`
        
    - `0x4` ^ `0xf` = `0xb`
        
    - `0xe` ^ `0x4` = `0xa`
        
        _Current state: `ax = 0x9fba`_
        

The function finishes by executing `pop ebp` and `ret`, outputting the final value residing in the accumulator register (`eax`), which is **`0x9fba`**.
## Referencias
https://carlosrafaelgn.com.br/Asm86/