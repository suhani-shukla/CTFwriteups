# Glory Of The Garden


Challenge gives you `garden.jpg`. Hint points at a hex editor.

## Recon / first look

Skipped the hex editor, went straight for strings:

```bash
strings garden.jpg | grep pico
```

## The bug / trick

Flag was just sitting in the file as plaintext, no need to actually dig through hex.

## Flag

```
picoCTF{redacted}
```