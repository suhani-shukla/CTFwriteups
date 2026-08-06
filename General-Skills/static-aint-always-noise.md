# Static ain't always noise

## Challenge
Look at the data in the `static` binary. The `ltdis.sh` bash script might help.

## Hints
TODO

## Solution
1. TODO (downloaded `static` binary and `ltdis.sh` script; exact usage of `ltdis.sh` not detailed).
2. Extracted printable strings from the `static` binary and filtered for the flag prefix:
```
   strings static | grep "pico"
```
3. This directly returned the flag.

## Flag
```
picoCTF{d15a5m_t34s3r_20335e41}
```