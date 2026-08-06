# convertme.py

## Challenge
General Skills, Easy. Run the Python script and convert the given number from decimal to binary to get the flag.

## Hints
1. Look up a decimal to binary number conversion app on the web or use your computer's calculator!
2. The `str_xor` function does not need to be reverse engineered for this challenge.
3. If you have Python on your computer, you can download the script normally and run it. Otherwise, use `wget` in the webshell.
4. To use `wget` in the webshell, first right click on the download link and select 'Copy Link' or 'Copy Link Address'.
5. Type `wget` followed by the copied link in the webshell and press enter to download the script.
6. Run the script with `python3 convertme.py`.

## Solution
1. Downloaded and ran the script:
```
   python convertme.py
```
2. The script generated a random decimal number and prompted for its binary equivalent:
```
   If 26 is in decimal base, what is it in binary base?
```
3. Converted the number using an online decimal-to-binary converter and submitted the answer:
```
   Answer: 11010
```
4. The script validated the answer and printed the flag directly to the terminal.

## Flag
```
picoCTF{4ll_y0ur_b4535_9c3b7d4d}
```