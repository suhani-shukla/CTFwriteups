# Disk, Disk, Sleuth

## Challenge
Use `srch_strings` from The Sleuth Kit and some terminal-fu to find a flag in the disk image `dds1-alpine.flag.img.gz`.

## Hints
1. Have you ever used `file` to determine what a file was?
2. Relevant terminal-fu in picoGym: `https://play.picoctf.org/practice/challenge/85`
3. Mastering this terminal-fu enables finding the flag in a single command: `https://play.picoctf.org/practice/challenge/48`
4. Using your own computer, `qemu` could be used to boot from this disk.

## Solution
1. Extracted the gzip-compressed disk image:
```
   gunzip dds1-alpine.flag.img.gz
```
2. Confirmed the file type and partition layout:
```
   file dds1-alpine.flag.img
```
   Output:
```
   dds1-alpine.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0x10,81,1), startsector 2048, 260096 sectors
```
3. Attempted to search the image for the flag using `srch_string`, which failed since the correct binary name is `srch_strings`:
```
   srch_string dds1-alpine.flag.img | grep "pico"
```
4. Located the correct binary:
```
   which srch_strings
```
   Output: `/usr/bin/srch_strings`
5. Ran `srch_strings` directly on the raw disk image (without mounting it) and filtered for the flag prefix:
```
   /usr/bin/srch_strings dds1-alpine.flag.img | grep "pico"
```
6. Among a few unrelated kernel symbol matches, the output included the flag embedded in what appears to be a boot/init script line (`SAY picoCTF{...}`).

## Flag
```
picoCTF{f0r3ns1c4t0r_n30phyt3_5e56e786}
```