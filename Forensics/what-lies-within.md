# What Lies Within

## Challenge
There's something in the building. Retrieve the flag from `buildings.png`.

## Hints
1. There is data encoded somewhere — there might be an online decoder.

## Solution
1. Checked the image metadata for hidden clues:
```
   exiftool buildings.png
```
   Output showed standard PNG metadata (657x438, RGB with Alpha, Deflate/Inflate compression) with nothing unusual in the metadata fields.
2. Ran `zsteg` against the image to scan bit-plane/channel combinations for hidden data:
```
   zsteg buildings.png
```
3. The `b1,rgb,lsb,xy` plane contained readable text directly matching the flag format:
```
   b1,rgb,lsb,xy       .. text: "picoCTF{h1d1ng_1n_th3_b1t5}"
```

## Flag
```
picoCTF{h1d1ng_1n_th3_b1t5}
```