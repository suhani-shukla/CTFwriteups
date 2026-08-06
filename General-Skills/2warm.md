# 2warm

## Challenge
Can you convert the number 42 (base 10) to binary (base 2)? Doable in-browser with CyberChef.

## Hints
1. TODO

## Solution
```
echo "obase=2; 42" | bc
101010
```
Converted decimal to binary with `bc`.

## Flag
```
picoCTF{101010}
```