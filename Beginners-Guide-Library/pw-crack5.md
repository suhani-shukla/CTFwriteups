# PW Crack 5

## Challenge
General Skills. Crack the password to get the flag using `level5.py`, the encrypted flag file, and the hash file, all in the same directory. A `dictionary.txt` wordlist is provided containing all possible passwords based on the conventions seen in previous levels.

## Hints
1. Opening a file in Python is crucial to using the provided dictionary.
2. You may need to trim whitespace from the dictionary word before hashing — look up Python's `strip` string function.
3. The `str_xor` function does not need to be reverse engineered for this challenge.

## Solution
1. Inspected the checker script and binary files, noting that `level5.py` hashes a candidate password and compares it against a stored hash in `level5.hash.bin`, which is in raw binary form.
2. Converted the binary hash to a readable hex string:
```
   xxd -p level5.hash.bin
```
3. Wrote a script, `pass.py`, to hash every word in `dictionary.txt` with MD5 and print each word alongside its hash:
```python
   import hashlib

   with open('dictionary.txt', 'r') as f:
       passlist = f.read().splitlines()

   def hash_pw(pw_str):
       pw_bytes = bytearray()
       pw_bytes.extend(pw_str.encode())
       m = hashlib.md5()
       m.update(pw_bytes)
       return m.digest()

   for pw in passlist:
       print(pw, hash_pw(pw).hex())
```
4. Ran the script and filtered the output for the hex hash obtained from `level5.hash.bin`:
```
   python pass.py | grep e8352e76e260a31eb266012f70df9a10
```
   Output:
```
   7e5f e8352e76e260a31eb266012f70df9a10
```
5. This identified `7e5f` as the correct password. Piped it into the checker script:
```
   echo 7e5f | python level5.py
```
6. The script validated the password and printed the flag directly to the terminal.

## Flag
```
picoCTF{h45h_sl1ng1ng_40f26f81}
```