# Wave a flag

## Challenge
Invoke help flags for a tool/binary (`warm`). Program has extraordinarily helpful information.

## Hints
1. Only works in webshell or another Linux computer.
2. Get the file with `wget <URL here>` (URL in details section).
3. Run with `./warm`, make executable first with `chmod +x warm`.
4. `-h` and `--help` are the most common arguments to get more info.
5. Not every program implements help features like `-h` and `--help`.

## Solution
```
chmod +x warm
./warm -h
```
Ran `warm` with `-h` flag, printed the flag directly.

## Flag
```
picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}
```