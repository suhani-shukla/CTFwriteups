# First Grep

## Challenge
Find the flag in the file. Tedious to look through manually — there's a better way.

## Hints
1. grep tutorial

## Solution
```
strings file | grep "picoCTF"
picoCTF{grep_is_good_to_find_things_29f42460}
```
Ran `strings` on the file, grepped for `picoCTF` to pull the flag.

## Flag
```
picoCTF{grep_is_good_to_find_things_29f42460}
```