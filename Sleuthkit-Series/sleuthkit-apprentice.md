# Sleuthkit Apprentice

## Challenge
Download the disk image and find the flag. If using the webshell, extract the disk image into `/tmp`, not the home directory.

## Hints
TODO

## Solution
1. Extracted the compressed disk image:
```
   gunzip disk.flag.img.gzip
```
2. Listed the partition table to identify all partitions and their offsets:
```
   mmls disk.flag.img
```
   Output showed three partitions: a Linux partition at sector `2048`, a Linux Swap partition at `206848`, and a second Linux partition at `360448`.
3. Recursively listed files in the first Linux partition (offset `2048`), which did not contain any useful files:
```
   fls -r -o 2048 disk.img.flag
```
4. Recursively listed files in the second Linux partition (offset `360448`):
```
   fls -r -o 360448 disk.img.flag
```
   This revealed `my_folder` containing `flag.txt` (a reallocated/deleted entry) and `flag.uni.txt`, an intact file with inode `2371`.
5. Extracted the contents of `flag.uni.txt` using its inode number:
```
   icat -o 360448 disk.flag.img 2371
```
   This returned the flag directly.

## Flag
```
picoCTF{by73_5urf3r_2f22df38}
```