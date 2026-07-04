# Enahnce! 


Challenge gives you `drawing.flag.svg`.

## Recon / first look

SVG is just XML, so:

```bash
cat drawing.flag.svg
```

## The bug / trick

Flag was broken up into pieces scattered through the file, sitting in plain sight once you actually read the markup.

## Flag

```
picoCTF{redacted}
```