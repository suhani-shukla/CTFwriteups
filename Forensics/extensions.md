# extensions

## Challenge
A really weird text file. Find the flag in `TXT`.

## Hints
1. How do operating systems know what kind of file it is? It's not just the ending.
2. Make sure to submit the flag as `picoCTF{XXXXX}`.

## Solution
1. Downloaded the file and listed the directory:
```
   ls
```
   Found `flag.txt`.
2. Checked the actual file type rather than trusting the `.txt` extension:
```
   file flag.txt
```
   Output:
```
   flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced
```
   The file was actually a PNG image mislabeled with a `.txt` extension.
3. Renamed the file with the correct extension so it could be opened as an image:
```
   mv flag.txt flag.png
```
4. Opened `flag.png`, which displayed the flag as image text.

## Flag
```
picoCTF{now_you_know_about_extensions}
```