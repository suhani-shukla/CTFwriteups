# st3g0

## Challenge
Download the image and find the flag.

## Hints
1. The end sequence of the message will be `$t3g0`.

## Solution
1. Ran `zsteg` against the downloaded image to scan all bit-plane/channel combinations for hidden data:
```
   zsteg pico.flag.png
```
2. Among the many bit-plane results, the `b1,rgb,lsb,xy` plane contained readable text matching the flag format and ending in the sequence given by the hint:
```
   b1,rgb,lsb,xy       .. text: "picoCTF{7h3r3_15_n0_5p00n_96ae0ac1}$t3g0"
```
3. Extracted the flag portion, discarding the trailing `$t3g0` marker.

## Flag
```
picoCTF{7h3r3_15_n0_5p00n_96ae0ac1}
```