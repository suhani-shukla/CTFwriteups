# strings it

## Challenge
Find the flag in file `strings` without running it.

## Hints
1. `strings`

## Solution
```
file strings
strings: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=73f2d464627f38e9206addd1f490a0cb09ac7dc5, for GNU/Linux 3.2.0, not stripped
```
```
strings strings | grep "pico"
picoCTF{5tRIng5_1T_dB2CEA76}
```
Ran `strings` on the binary, grepped for `pico` to pull the flag without executing it.

## Flag
```
picoCTF{5tRIng5_1T_dB2CEA76}
```