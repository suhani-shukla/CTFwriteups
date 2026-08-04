# PW Crack 4

## Challenge
General Skills. Crack the password to get the flag using `level4.py`, the encrypted flag file, and the hash file, all in the same directory. There are 100 potential passwords, only 1 of which is correct.

## Hints
1. A `for` loop can help you do many things very quickly.
2. The `str_xor` function does not need to be reverse engineered for this challenge.

## Solution
1. Viewed the source of the checker script:
```
   cat level4.py
```
2. Found a hardcoded list (`pos_pw_list`) of 100 candidate passwords embedded in the script, similar in structure to previous levels in the series but too large to try one at a time by hand.
3. Extracted the list into a standalone `words.txt` file, one password per line, using Python:
```
   python -c 'pos_pw_list = ["8c86", "7692", "a519", ... "a7e2"]; open("words.txt","w").write("\n".join(pos_pw_list))'
```
4. Automated password testing with a bash loop that fed each candidate from `words.txt` into `level4.py`:
```bash
   while read pw; do
       echo "$pw" | python level4.py
   done < words.txt
```
5. Most attempts returned `That password is incorrect`. One candidate returned `Welcome back... your flag, user:` followed by the decrypted flag, confirming the correct password and completing the loop over the remaining candidates.

## Flag
```
picoCTF{fl45h_5pr1ng1ng_d770d48c}
```