# Sleuthkit Intro

## Challenge
Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check the answer and get the flag. If using the webshell, extract the disk image into `/tmp`, not the home directory.

Checker: `nc saturn.picoctf.net 57264`

## Hints
TODO

## Solution
1. Downloaded the disk image, which was gzip-compressed, and extracted it:
```
   gunzip disk.img.gz
```
2. Connected to the checker service and made an initial guess of `9` sectors, which was incorrect:
```
   nc saturn.picoctf.net 57264
   What is the size of the Linux partition in the given disk image?
   Length in sectors: 9
   That is not correct. Feel free to try again.
```
3. Inspected the disk image's partition table:
```
   file disk.img
```
   Output:
```
   disk.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0xc,190,50), startsector 2048, 202752 sectors
```
4. Confirmed the partition size with `fdisk`:
```
   fdisk -l disk.img
```
   Output showed the Linux partition (`disk.img1`, type `83 Linux`) starting at sector `2048`, ending at `204799`, spanning `202752` sectors.
5. Reconnected to the checker and submitted the correct sector count:
```
   nc saturn.picoctf.net 57264
   What is the size of the Linux partition in the given disk image?
   Length in sectors: 202752
```
6. The checker confirmed the answer and returned the flag.

## Flag
```
picoCTF{mm15_f7w!}
```