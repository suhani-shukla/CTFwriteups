# keygenme-py

## Challenge
Reverse Engineering, Medium. Only file given is `keygenme-trial.py`.

## Hints
TODO

## Solution
1. Downloaded and analyzed `keygenme-trial.py`. Found the key components:
```python
   username_trial = "BENNETT"
   bUsername_trial = b"BENNETT"

   key_part_static1_trial = "picoCTF{1n_7h3_kk3y_of_"
   key_part_dynamic1_trial = "xxxxxxxx"
   key_part_static2_trial = "}"
   key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial
```
2. Examined the `check_key` function, which validates a submitted key against `key_full_template_trial`. The static prefix must match `key_part_static1_trial` exactly. The 8-character dynamic part is then checked one character at a time against specific indices of the SHA-256 hash of `username_trial`, in this non-sequential order: indices `4, 5, 3, 6, 2, 7, 1, 8`.
3. Wrote a solve script (`solve.py`) reproducing the same hash and printing each required character in the order the checker validates them:
```python
   import hashlib

   username_trial = "BENNETT"
   bUsername_trial = b"BENNETT"

   print(hashlib.sha256(bUsername_trial).hexdigest()[4])
   print(hashlib.sha256(bUsername_trial).hexdigest()[5])
   print(hashlib.sha256(bUsername_trial).hexdigest()[3])
   print(hashlib.sha256(bUsername_trial).hexdigest()[6])
   print(hashlib.sha256(bUsername_trial).hexdigest()[2])
   print(hashlib.sha256(bUsername_trial).hexdigest()[7])
   print(hashlib.sha256(bUsername_trial).hexdigest()[1])
   print(hashlib.sha256(bUsername_trial).hexdigest()[8])
```
4. Ran the script:
```
   python solve.py
```
   Output:
```
   0
   8
   c
   4
   6
   a
   a
   4
```
5. Concatenated the output characters (`08c46aa4`) into the dynamic part of the flag template, forming the complete key/flag: `picoCTF{1n_7h3_kk3y_of_08c46aa4}`.

## Flag
```
picoCTF{1n_7h3_kk3y_of_08c46aa4}
```