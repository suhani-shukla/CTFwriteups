# Bit-O-Asm-3

## Challenge
Reverse engineering challenge — given an assembly dump, figure out what's in the `eax` register at the end of the function and convert it to decimal for the flag. picoCTF.

## Hints
1. Not everything in this disassembly listing is optimal.

## Solution
Dumped the disassembly with `cat disassembler-dump0_c.txt`:

```asm
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0xc],0x9fe1a
<+22>:    mov    DWORD PTR [rbp-0x8],0x4
<+29>:    mov    eax,DWORD PTR [rbp-0xc]
<+32>:    imul   eax,DWORD PTR [rbp-0x8]
<+36>:    add    eax,0x1f5
<+41>:    mov    DWORD PTR [rbp-0x4],eax
<+44>:    mov    eax,DWORD PTR [rbp-0x4]
<+47>:    pop    rbp
<+48>:    ret
```

More going on this time: `0x9fe1a` and `0x4` get stashed in two stack slots, then `eax` is loaded with the first, multiplied (`imul`) by the second, and `0x1f5` gets added on top. The result gets stored back to the stack and immediately reloaded into `eax` before returning — that last store/reload doesn't change the value, just shuffles it through memory.

Worked it out piece by piece:

```bash
printf "%d\n" 0x9fe1a
```
```
654874
```

```bash
printf "%d\n" 0x4
```
```
4
```

Tried to do it all in one line and hit a bash syntax error on the arithmetic expansion:

```bash
echo $((0x9fe1a*0x4)+(0x1f5))
```
```
bash: command substitution: line 1: syntax error near unexpected token `+(0x1f5)'
bash: command substitution: line 1: `(0x9fe1a*0x4)+(0x1f5)'
```

Split it up instead — multiply first:

```bash
echo $((0x9fe1a*0x4))
```
```
2619496
```

Then converted `0x1f5`:

```bash
printf "%d\n" 0x1f5
```
```
501
```

And added it on:

```bash
echo $((2619496+501))
```
```
2619997
```

## Flag
```
picoCTF{2619997}
```