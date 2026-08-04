# Python Wrangling

## Challenge
General Skills, Medium. Run `ende.py` using `password.txt` to get `flag.txt.en`.

## Hints
1. Get the Python script accessible in your shell with `wget` followed by the link from the details section.
2. `man python`

## Solution
1. Downloaded the challenge files (`ende.py`, `password.txt`, `flag.txt.en`) into the working directory.
2. Checked the contents of `password.txt` to identify the password needed for encryption/decryption:
```
   cat password.txt
   720b6ad346f84cd483c60c7464dd95d4
```
3. Opened `ende.py` to understand how it works — it's a Fernet-based encryption/decryption tool that takes a password and a file, and supports `-e` (encrypt) and `-d` (decrypt) modes.
4. Ran the script in encrypt mode on `password.txt` itself as a test, to confirm the tool's behavior before touching the actual flag file:
```
   python ende.py -e password.txt
```
   When prompted, entered the password from step 2. The script produced a long encrypted token:
```
   gAAAAABqcerSPyEnnmdeUlf3q7xCLYhXkcfpl380B5gXEaaAppLqN_wPlxezFTjLGf7pUALjyz3AIVF3dTSLnWQzCL_bQ8SWnvXmY7LoPVP7aTCSf8tQnEkm-loZ91uNJOg-Zh1JVNkR
```
5. Checked `python ende.py -h` to confirm the correct flag and argument order for decrypting a file.
6. Ran the script in decrypt mode on the actual target file:
```
   python ende.py -d flag.txt.en
```
7. When prompted for the password, entered the same password from `password.txt`. The script decrypted the file and printed the flag directly to the terminal.

## Flag
```
picoCTF{4p0110_1n_7h3_h0us3_9c5f9bcf}
```