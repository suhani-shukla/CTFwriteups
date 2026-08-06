# Magikarp Ground Mission

## Challenge
Move between directories and read files in the shell. Start the container, SSH to it, and `ls` once connected to begin. Login via `ssh` as `ctf-player` with password `8c606eb1` on host `wily-courier.picoctf.net`, port `56261`.

## Hints
1. Finding a cheatsheet for bash would be really helpful!

## Solution
1. Connected to the instance via SSH:
```
   ssh ctf-player@wily-courier.picoctf.net -p 64498
```
   Accepted the host key and authenticated with the given password.
2. Listed the home directory contents:
```
   ls
```
   Found `1of3.flag.txt` and `instructions-to-2of3.txt`.
3. Read the instructions file for the next step:
```
   cat instructions-to-2of3.txt
```
   Output: `Next, go to the root of all things, more succinctly /`
4. Confirmed the file type and read the first part of the flag:
```
   file 1of3.flag.txt
   cat 1of3.flag.txt
```
   Output: `picoCTF{xxsh_`
5. Moved up a directory and listed contents:
```
   cd ..
   ls
```
   Found `3of3.flag.txt` and a `drop-in` directory.
6. Read the third part of the flag (found out of order):
```
   cat 3of3.flag.txt
```
   Output: `0b24fc4f}`
7. Explored `drop-in`, which turned out to be a decoy containing the same files as the home directory:
```
   cd drop-in
   ls
   pwd
```
8. Navigated back up and continued toward root as instructed:
```
   cd ..
   cd ..
   ls
   pwd
```
   Reached `/home`.
9. Continued to the filesystem root:
```
   cd ..
   ls
```
   Found `2of3.flag.txt` and `instructions-to-3of3.txt` at `/`.
10. Read the second part of the flag:
```
    cat 2of3.flag.txt
```
    Output: `0ut_0f_//4t3r_`
11. Assembled all three parts in order (1of3 + 2of3 + 3of3) to form the complete flag.

## Flag
```
picoCTF{xxsh_0ut_0f_//4t3r_0b24fc4f}
```