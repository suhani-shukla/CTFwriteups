# Disk, Disk, Sleuth II

## Challenge
The file with the flag is named `down-at-the-bottom.txt`. Disk image: `dds2-alpine.flag.img.gz`.

## Hints
1. The Sleuth Kit has some great tools for this challenge as well.
2. Sleuthkit docs: TSK Tool Overview.
3. This disk can also be booted with `qemu`.

## Solution
1. Extracted the gzip-compressed disk image:
```
   gunzip dds2-alpine.flag.img.gz
```
2. Confirmed the file type:
```
   file dds2-alpine.flag.img
```
   Output confirmed a DOS/MBR boot sector with one partition, start sector `2048`, `260096` sectors.
3. Listed the partition table to get the exact partition offset:
```
   mmls dds2-alpine.flag.img
```
   Confirmed the Linux partition (`0x83`) starts at sector `2048`.
4. Listed the top-level file/directory structure of the partition using the offset:
```
   fls -o 2048 dds2-alpine.flag.img
```
   This showed only top-level entries (standard Linux root directories), not the target file.
5. Recursively listed all files in the partition and filtered for the target filename:
```
   fls -r -o 2048 dds2-alpine.flag.img | grep down-at-the-bottom.txt
```
   Output:
```
   + r/r 18291: down-at-the-bottom.txt
```
   This gave the inode number (`18291`) of the target file.
6. Extracted the file's contents directly from the disk image using its inode number:
```
   icat -o 2048 dds2-alpine.flag.img 18291
```
   The output displayed the flag in ASCII-art bubble-letter formatting, one character per box, spelling out the flag.

## Flag
```
picoCTF{f0r3ns1c4t0r_n0vic3_4bd721f2}
```