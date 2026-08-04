# PW Crack 3

## Challenge
General Skills. Crack the password to get the flag using `level3.py`, the encrypted flag file, and `level3.hash.bin`, all in the same directory. There are 7 potential passwords, only 1 of which is correct.

## Hints
1. To view `level3.hash.bin` in the webshell: `bvi level3.hash.bin`
2. To exit `bvi`, type `:q` and press enter.
3. The `str_xor` function does not need to be reverse engineered for this challenge.

## Solution
1. Viewed the source of the checker script:
```
   cat level3.py
```
2. The script reads `level3.flag.txt.enc` and `level3.hash.bin`, hashes the user's input password with MD5, and compares it against `correct_pw_hash` (loaded from `level3.hash.bin`). If it matches, it XOR-decrypts the flag with the entered password using `str_xor`.
3. At the bottom of the script, found a list of 7 candidate passwords left in a comment:
```python
   pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]
```
4. Since only one password's MD5 hash matches `level3.hash.bin`, tried each candidate against the running script until the correct one was found:
```
   python level3.py
   Please enter correct password for flag: 4e66
   That password is incorrect
```
5. Continued trying candidates:
```
   python level3.py
   Please enter correct password for flag: 865e
   Welcome back... your flag, user:
```
6. `865e` matched the stored hash, and the script decrypted and printed the flag.

## Flag
```
picoCTF{m45h_fl1ng1ng_2b072a90}
```