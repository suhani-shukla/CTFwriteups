# Bit-O-Asm-1

## Challenge
Reverse engineering challenge — given an assembly dump, figure out what's in the `eax` register at the end of the function and convert it to decimal for the flag. picoCTF.

## Hints
1. Lots of noise in the disassembly. Find the one line that matters and don't second-guess it.

## Solution
Dumped the disassembly with `cat disassembler-dump0_a.txt`:

```asm
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x4],edi
<+11>:    mov    QWORD PTR [rbp-0x10],rsi
<+15>:    mov    eax,0x30
<+20>:    pop    rbp
<+21>:    ret
```

The prologue just sets up the stack frame and stashes the args (`edi`, `rsi`) — none of that touches `eax`. The line that actually matters is `mov eax,0x30`, which loads `0x30` straight into `eax` right before the function returns it.

Converted `0x30` to decimal:

```bash
printf "%d\n" 0x30
```

```
48
```

## Flag
```
picoCTF{48}
```