# First Find

## Challenge
Unzip the provided archive and find the file named `uber-secret.txt`.

## Hints
TODO

## Solution
1. Listed the contents of the archive without extracting, to preview the file structure:
```
   unzip -l files.zip
```
2. Extracted the archive:
```
   unzip files.zip
```
3. Navigated through the nested directory structure to locate the target file:
```
   cd files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets
   ls
```
   Found `uber-secret.txt` in this directory.
4. Read the file to retrieve the flag:
```
   cat uber-secret.txt
```

## Flag
```
picoCTF{f1nd_15_f457_ab443fd1}
```