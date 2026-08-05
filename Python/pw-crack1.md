# PW Crack 1

## Challenge
General Skills, Easy. Crack the password to get the flag using `level1.py` and the encrypted flag file in the same directory.

## Hints
1. To view the file in the webshell: `nano level1.py`
2. To exit nano, press `Ctrl+x` and follow the on-screen prompts.
3. The `str_xor` function does not need to be reverse engineered for this challenge.

## Solution
1. Listed the working directory to confirm both `level1.py` and `level1.flag.txt.enc` were present.
2. Viewed the encrypted flag file to see what it looked like before decryption:
```
   cat level1.flag.txt.enc
```
   Output was unreadable binary/garbled text, confirming it was encrypted.
3. Viewed the source of the checker script to understand how the password is validated and how decryption happens:
```
   cat level1.py
```
4. While reading through `level1.py`, found the correct password hardcoded directly in the source: `1e1a`. Per hint 3, the `str_xor` function used internally for decryption didn't need to be reverse engineered — just supplying the correct password was enough.
5. Ran the script:
```
   python level1.py
```
6. When prompted with `Please enter correct password for flag:`, entered `1e1a`.
7. The script validated the password, decrypted `level1.flag.txt.enc` internally, and printed the flag directly to the terminal.

## Flag
```
picoCTF{545h_r1ng1ng_fa343060}
```