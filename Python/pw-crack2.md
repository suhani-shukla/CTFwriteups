# PW Crack 2

## Challenge
General Skills, Easy. Crack the password to get the flag using `level2.py` and the encrypted flag file in the same directory.

## Hints
1. Does that encoding look familiar?
2. The `str_xor` function does not need to be reverse engineered for this challenge.

## Solution
1. Downloaded the challenge files and viewed the source of the checker script:
```
   cat level2.py
```
2. Found the password hardcoded in the script, but encoded as hex character codes rather than plain text:
```
   chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36)
```
3. Decoded it by running the same expression directly in Python:
```
   python3 -c "print(chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36))"
```
   Output:
```
   de76
```
4. Ran the checker script:
```
   python level2.py
```
5. When prompted with `Please enter correct password for flag:`, entered `de76`.
6. The script validated the password and printed the flag directly to the terminal.

## Flag
```
picoCTF{tr45h_51ng1ng_489dea9a}
```