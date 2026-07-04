# Information

**CTF:** picoCTF

Challenge gives you a single file, `cat.jpg`.

## Recon / first look

Downloaded the image and ran:

```bash
exiftool cat.jpg
```

Dumped the metadata. Nothing screamed "flag" at first glance, but the `License` field had a chunk of base64 sitting in it.

## The bug / trick

Flag was stashed in the EXIF `License` field, base64-encoded.

## Exploitation

Decoded it:

```bash
echo "(...insert coded text...)" | base64 -d
```

Flag popped right out.

## Flag

```
picoCTF{redacted}
```