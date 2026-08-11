# caesar

## Challenge
Crypto challenge — decrypt a Caesar-shifted message.

## Hints
1. Caesar cipher tutorial.

## Solution
Checked the file type first:

```bash
file data.enc
```
```
data.enc: ASCII text
```

Plain ASCII, so just `cat`'d it:

```bash
cat data.enc
```
```
picoCTF{furvvlqjwkhuxelfrqslandktj}
```

Looks like a Caesar-shifted flag — `picoCTF{` itself is still readable so the shift is small, but rather than eyeball it, brute-forced all 26 shifts with a one-liner:

```bash
for i in {0..25}; do echo "Shift $i: $(echo 'picoCTF{furvvlqjwkhuxelfrqslandktj}' | python3 -c "import sys; s=$i; print(''.join(chr((ord(c)-97-s)%26+97) if 'a'<=c<='z' else c for c in sys.stdin.read()))")"; done
```
```
Shift 0: picoCTF{furvvlqjwkhuxelfrqslandktj}
Shift 1: ohbnCTF{etquukpivjgtwdkeqprkzmcjsi}
Shift 2: ngamCTF{dspttjohuifsvcjdpoqjylbirh}
Shift 3: mfzlCTF{crossingtherubiconpixkahqg}
Shift 4: leykCTF{bqnrrhmfsgdqtahbnmohwjzgpf}
Shift 5: kdxjCTF{apmqqglerfcpszgamlngviyfoe}
Shift 6: jcwiCTF{zolppfkdqeboryfzlkmfuhxend}
Shift 7: ibvhCTF{ynkooejcpdanqxeykjletgwdmc}
Shift 8: haugCTF{xmjnndiboczmpwdxjikdsfvclb}
Shift 9: gztfCTF{wlimmchanbylovcwihjcreubka}
Shift 10: fyseCTF{vkhllbgzmaxknubvhgibqdtajz}
Shift 11: exrdCTF{ujgkkafylzwjmtaugfhapcsziy}
Shift 12: dwqcCTF{tifjjzexkyvilsztfegzobryhx}
Shift 13: cvpbCTF{sheiiydwjxuhkrysedfynaqxgw}
Shift 14: buoaCTF{rgdhhxcviwtgjqxrdcexmzpwfv}
Shift 15: atnzCTF{qfcggwbuhvsfipwqcbdwlyoveu}
Shift 16: zsmyCTF{pebffvatgurehovpbacvkxnudt}
Shift 17: yrlxCTF{odaeeuzsftqdgnuoazbujwmtcs}
Shift 18: xqkwCTF{nczddtyrespcfmtnzyativlsbr}
Shift 19: wpjvCTF{mbyccsxqdrobelsmyxzshukraq}
Shift 20: voiuCTF{laxbbrwpcqnadkrlxwyrgtjqzp}
Shift 21: unhtCTF{kzwaaqvobpmzcjqkwvxqfsipyo}
Shift 22: tmgsCTF{jyvzzpunaolybipjvuwperhoxn}
Shift 23: slfrCTF{ixuyyotmznkxahoiutvodqgnwm}
Shift 24: rkeqCTF{hwtxxnslymjwzgnhtsuncpfmvl}
Shift 25: qjdpCTF{gvswwmrkxlivyfmgsrtmboeluk}
```

Note the shift script isn't even touching the `CTF{...}` wrapper (it only shifts `a-z`), so the wrapper stays garbage on every line except the one where the shift lines up with the actual cipher — `Shift 3` is the only line that reads as real English: `crossingtherubicon`.

## Flag
```
picoCTF{crossingtherubiconpixkahqg}
```