# plumbing

## Challenge
General Skills, Medium. Find a way to keep the output from a program and search for the flag. Connect to `fickle-tempest.picoctf.net 57138`.

## Hints
1. Remember the flag format is `picoCTF{XXXX}`.
2. What's a pipe? This kind: `|`

## Solution
1. Connected to the service and piped its output directly into `grep` to filter for the flag, instead of manually reading through the full output:
```
   nc fickle-tempest.picoctf.net 57138 | grep "pico"
```
2. The piped output isolated the line containing the flag.

## Flag
```
picoCTF{digital_plumb3r_8c8f3412}
```