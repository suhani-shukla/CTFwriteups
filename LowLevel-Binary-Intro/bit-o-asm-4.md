# Bit-O-Asm-4

## Challenge
Reverse engineering challenge — given an assembly dump with a compare/jump branch, figure out what's in the `eax` register at the end of the function and convert it to decimal for the flag. picoCTF.

## Hints
1. Don't tell anyone I told you this, but you can solve this problem without understanding the compare/jump relationship.
2. Of course, if you're really good, you'll only need one attempt to solve this problem.

## Solution
Dumped the disassembly with `cat disassembler-dump0_d.txt`:

```asm
<+0>:     endbr64 
<+4>:     push   rbp
<+5>:     mov    rbp,rsp
<+8>:     mov    DWORD PTR [rbp-0x14],edi
<+11>:    mov    QWORD PTR [rbp-0x20],rsi
<+15>:    mov    DWORD PTR [rbp-0x4],0x9fe1a
<+22>:    cmp    DWORD PTR [rbp-0x4],0x2710
<+29>:    jle    0x55555555514e <main+37>
<+31>:    sub    DWORD PTR [rbp-0x4],0x65
<+35>:    jmp    0x555555555152 <main+41>
<+37>:    add    DWORD PTR [rbp-0x4],0x65
<+41>:    mov    eax,DWORD PTR [rbp-0x4]
<+44>:    pop    rbp
<+45>:    ret
```

Starts by stashing `0x9fe1a` on the stack, then `cmp`s it against `0x2710` and branches on `jle`. Converted both first to see which side of the branch actually gets taken:

```bash
printf "%d\n" 0x9fe1a
```
```
654874
```

```bash
printf "%d\n" 0x2710
```
```
10000
```

`654874` is not `<= 10000`, so the `jle` doesn't fire — execution falls straight through to `sub DWORD PTR [rbp-0x4],0x65`, skipping the `add` branch entirely. No need to trace the jump logic, just needed to know which path the numbers actually take.

```bash
printf "%d\n" 0x65
```
```
101
```

```bash
echo $((654874-101))
```
```
654773
```

## Flag
```
picoCTF{654773}
```