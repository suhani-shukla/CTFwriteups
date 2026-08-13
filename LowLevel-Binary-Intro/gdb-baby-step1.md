# GDB baby step 1

## Challenge
Reverse engineering challenge — disassemble a binary with `gdb` and figure out what's in `eax` at the end of `main`. picoCTF.

## Hints
1. `gdb` is a very good debugger to use for this problem and many others!
2. `main` is actually a recognized symbol that can be used with `gdb` commands.

## Solution
Loaded the binary into `gdb`:

```bash
gdb debugger0_a
```

Listed functions to confirm `main` is a usable symbol:

```
(gdb) info functions
```

Switched to Intel syntax (easier to read than AT&T) and disassembled `main`:

```
(gdb) set disassembly-flavor intel
(gdb) disassemble main
```
```
Dump of assembler code for function main:
   0x0000000000001129 <+0>:     endbr64
   0x000000000000112d <+4>:     push   rbp
   0x000000000000112e <+5>:     mov    rbp,rsp
   0x0000000000001131 <+8>:     mov    DWORD PTR [rbp-0x4],edi
   0x0000000000001134 <+11>:    mov    QWORD PTR [rbp-0x10],rsi
   0x0000000000001138 <+15>:    mov    eax,0x86342
   0x000000000000113d <+20>:    pop    rbp
   0x000000000000113e <+21>:    ret
End of assembler dump.
```

Same pattern as the Bit-O-Asm series — prologue sets up the stack frame, `eax` gets loaded directly with `0x86342`, then it's returned. Used `gdb`'s own `print` to convert straight to decimal instead of dropping to a shell:

```
(gdb) print 0x86342
$1 = 549698
```

## Flag
```
picoCTF{549698}
```