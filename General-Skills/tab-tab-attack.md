# Tab, Tab, Attack

## Challenge
Using tabcomplete adds years to your life, esp. with long rambling directory structures and filenames. File: `Addadshashanammu.zip`.

## Hints
1. After unzipping, solvable with 11 button-presses (mostly `Tab`).

## Solution
```
unzip -l Addadshashanammu.zip
unzip Addadshashanammu.zip
```
Nested folders found from the listing, path copied via tabcomplete:
```
cd Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/
ls Ularradallaku
```
Found a C source file:
```
cat fang-of-haynekhtnamet.c
```
```c
#include <stdio.h>

int main(){
printf("*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}\n");
}
```
Flag was hardcoded in the source.

## Flag
```
picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}
```