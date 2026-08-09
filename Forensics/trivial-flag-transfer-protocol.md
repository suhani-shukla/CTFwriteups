# Trivial Flag Transfer Protocol

## Challenge
Figure out how they moved the flag. File: `tftp.pcapng`.

## Hints
1. What are some other ways to hide data?

## Solution
Opened `tftp.pcapng` in Wireshark, filtered on `tftp.type`, then exported all objects via `File > Export Objects`:
```
ls
instructions.txt  picture1.bmp  picture2.bmp  picture3.bmp  plan  program.deb  tftp.pcapng
```
`plan` was ROT13-encoded:
```
cat plan
VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF

echo 'VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF' | tr 'A-Za-z' 'N-ZA-Mn-za-m'
IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS
```
`instructions.txt` was also ROT13:
```
cat instructions.txt
GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA

echo "GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN
```
`program.deb` turned out to be `steghide`:
```
sudo apt install ./program.deb
```
Note, selecting 'steghide' instead of './program.deb'.

Extracted hidden data from the `.bmp` files using the passphrase `DUEDILIGENCE` (case-sensitive, found via ROT13 decode):
```
steghide extract -sf picture1.bmp -p "DUEDILIGENCE"
steghide: could not extract any data with that passphrase!

steghide extract -sf picture2.bmp -p "DUEDILIGENCE"
steghide: could not extract any data with that passphrase!

steghide extract -sf picture3.bmp -p "DUEDILIGENCE"
wrote extracted data to "flag.txt".

cat flag.txt
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```

## Flag
```
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}
```