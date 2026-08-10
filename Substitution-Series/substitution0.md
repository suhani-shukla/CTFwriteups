# substitution0

## Challenge
Crypto challenge — a message encrypted with a monoalphabetic substitution cipher, with the cipher key given as the first line of the message itself.

## Hints
1. Try a frequency attack. An online tool might help.

## Solution
Downloaded the message. First line is the key — the ciphertext alphabet mapped onto the plaintext alphabet:

```
ZGSOCXPQUYHMILERVTBWNAFJDK
ABCDEFGHIJKLMNOPQRSTUVWXYZ
```

Rest of the message is the encrypted text:

```
Qctcnrel Mcptzlo ztebc, fuwq z ptzac zlo bwzwcmd zut, zlo gtenpqw ic wqc gccwmc
xtei z pmzbb szbc ul fqusq uw fzb clsmebco. Uw fzb z gcznwuxnm bsztzgzcnb, zlo, zw
wqzw wuic, nlhlefl we lzwntzmubwb—ex sentbc z ptczw rtukc ul z bsuclwuxus reulw
ex aucf. Wqctc fctc wfe tenlo gmzsh brewb lczt elc cjwtciuwd ex wqc gzsh, zlo z
melp elc lczt wqc ewqct. Wqc bszmcb fctc cjsccoulpmd qzto zlo pmebbd, fuwq zmm wqc
zrrcztzlsc ex gntlubqco pemo. Wqc fcupqw ex wqc ulbcsw fzb actd tcizthzgmc, zlo,
wzhulp zmm wqulpb ulwe selbuoctzwuel, U senmo qztomd gmzic Ynruwct xet qub eruluel
tcbrcswulp uw.

Wqc xmzp ub: ruseSWX{5NG5717N710L_3A0MN710L_357GX9XX}
```

Flipped the mapping around to go from ciphertext letter to plaintext letter directly:

```
ABCDEFGHIJKLMNOPQRSTUVWXYZ
VSEYOWBKMXZNLUDGHPCRIQTFJA
```

Ran the ciphertext through that substitution (frequency-attack style, matching the key) and got clean English out — an Edgar Allan Poe excerpt about the gold-bug beetle:

```
HEREUPON LEGRAND AROSE, WITH A GRAVE AND STATELY AIR, AND BROUGHT ME THE BEETLE
FROM A GLASS CASE IN WHICH IT WAS ENCLOSED. IT WAS A BEAUTIFUL SCARABAEUS, AND, AT
THAT TIME, UNKNOWN TO NATURALISTS—OF COURSE A GREAT PRIZE IN A SCIENTIFIC POINT
OF VIEW. THERE WERE TWO ROUND BLACK SPOTS NEAR ONE EXTREMITY OF THE BACK, AND A
LONG ONE NEAR THE OTHER. THE SCALES WERE EXCEEDINGLY HARD AND GLOSSY, WITH ALL THE
APPEARANCE OF BURNISHED GOLD. THE WEIGHT OF THE INSECT WAS VERY REMARKABLE, AND,
TAKING ALL THINGS INTO CONSIDERATION, I COULD HARDLY BLAME JUPITER FOR HIS OPINION
RESPECTING IT.

THE FLAG IS: PICOCTF{5UB5717U710N_3V0LU710N_357BF9FF}
```

## Flag
```
PICOCTF{5UB5717U710N_3V0LU710N_357BF9FF}
```