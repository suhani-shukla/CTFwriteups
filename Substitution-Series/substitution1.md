# substitution1

## Challenge
Crypto challenge — a second monoalphabetic substitution cipher, this time without the key handed over, so it's solved with a frequency attack.

## Hints
1. Try a frequency attack.
2. Do the punctuation and the individual words help you make any substitutions?

## Solution
Downloaded the message:

```
LKOb (bwvek ove lgqkhej kwj osgx) gej g kyqj vo lvrqhkje bjlhetky lvrqjktktvu. Lvukjbkgukb gej qejbjukjz dtkw g bjk vo lwgssjuxjb dwtlw kjbk kwjte lejgktftky, kjlwutlgs (guz xvvxstux) bitssb, guz qevmsjr-bvsftux gmtstky. Lwgssjuxjb hbhgssy lvfje g uhrmje vo lgkjxvetjb, guz dwju bvsfjz, jglw ytjszb g bketux (lgssjz g osgx) dwtlw tb bhmrtkkjz kv gu vustuj blvetux bjeftlj. LKOb gej g xejgk dgy kv sjgeu g dtzj geegy vo lvrqhkje bjlhetky bitssb tu g bgoj, sjxgs juftevurjuk, guz gej wvbkjz guz qsgyjz my rguy bjlhetky xevhqb gevhuz kwj dvesz ove ohu guz qeglktlj. Ove kwtb qevmsjr, kwj osgx tb: qtlvLKO{OE3AH3ULY_4774LI5_4E3_L001_6J0659OM}
```

No key given this time, but the flag format is predictable — every picoCTF flag starts `PICOCTF{`. Started there: matched `qtlvLKO{` in the ciphertext against `picoCTF{`, which pins down `q→p`, `t→i`, `l→c`, `v→o`, `L→C`, `K→T`, `O→F`. That's most of `P I C O T F` solved just from the flag wrapper alone.

From there, ran a frequency count on the rest of the ciphertext. The most frequent letter got substituted as `E`, and the next most frequent as `A` — filling in the remaining gaps in the alphabet mapping.

With the mapping complete, the ciphertext resolves cleanly:

```
CTFS (SHORT FOR CAPTURE THE FLAG) ARE A TYPE OF COMPUTER SECURITY COMPETITION. CONTESTANTS ARE PRESENTED WITH A SET OF CHALLENGES WHICH TEST THEIR CREATIVITY, TECHNICAL (AND GOOGLING) SKILLS, AND PROBLEM-SOLVING ABILITY. CHALLENGES USUALLY COVER A NUMBER OF CATEGORIES, AND WHEN SOLVED, EACH YIELDS A STRING (CALLED A FLAG) WHICH IS SUBMITTED TO AN ONLINE SCORING SERVICE. CTFS ARE A GREAT WAY TO LEARN A WIDE ARRAY OF COMPUTER SECURITY SKILLS IN A SAFE, LEGAL ENVIRONMENT, AND ARE HOSTED AND PLAYED BY MANY SECURITY GROUPS AROUND THE WORLD FOR FUN AND PRACTICE. FOR THIS PROBLEM, THE FLAG IS: PICOCTF{FR3*U3NCY_4774CK5_4R3_C001_6E0659FB}
```

## Flag
```
PICOCTF{FR3*U3NCY_4774CK5_4R3_C001_6E0659FB}
```