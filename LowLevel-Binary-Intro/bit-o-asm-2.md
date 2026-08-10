# Bit-O-Asm-2

## Challenge
Reverse engineering challenge — given an assembly dump, figure out what's in the `eax` register at the end of the function and convert it to decimal for the flag. picoCTF.

## Hints
1. `PTR`s, or "pointers", reference a location in memory where values can be stored.

## Solution
Dumped the disassembly with `cat disassembler-dump0_b.txt`:

```asm
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0x4],0x9fe1a
<+22>:    mov    eax,DWORD PTR [rbp-0x4]
<+25>:    pop    rbp
<+26>:    ret
```

This time `eax` isn't loaded with an immediate directly — `0x9fe1a` gets written into the stack slot at `[rbp-0x4]` first, then `mov eax,DWORD PTR [rbp-0x4]` reads it back out of memory into `eax` right before the return. Same end result, just routed through a pointer instead of a straight immediate load.

Converted `0x9fe1a` to decimal:

```bash
printf "%d\n" 0x9fe1a
```

```
654874
```

## Flag
```
picoCTF{654874}
```