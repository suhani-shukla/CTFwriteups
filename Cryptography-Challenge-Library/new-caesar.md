# New Caesar

## Challenge
Crypto challenge — a custom Vigenère-style cipher, but over a reduced 16-letter alphabet (`a`-`p`) instead of the usual 26, with the encoded bytes packed as base16-style pairs. Flag needs wrapping in `picoCTF{}`.

## Hints
1. How does the cipher work if the alphabet isn't 26 letters?
2. Even though the letters are split up, the same paradigms still apply.

## Solution
Given the ciphertext and `new_caesar.py`:

```
fegdeogdgecoeocgcgchcfcffccfca
```

TODO: contents of `new_caesar.py` (the encryption script) weren't included in the notes — only the ciphertext and the corresponding `solve.py`.

Wrote `solve.py` to reverse it. Key points from the script:

- `ALPHABET` is only the first 16 letters of `string.ascii_lowercase` (`a`-`p`), not the full 26 — matches hint 1 about a non-standard alphabet size.
- `b16_decode` takes the ciphertext two characters at a time, looks up each character's index in that 16-letter alphabet, formats each as 4 bits, concatenates the two nibbles into a byte, and converts that to a character — basically base16 decoding but using `a`-`p` instead of `0`-`f` as the digit symbols.
- `unshift` reverses a Vigenère-style shift: subtract the key character's alphabet index from the ciphertext character's index, mod 16 (the alphabet length) — same paradigm as a classic Caesar/Vigenère shift, just mod 16 instead of mod 26, which lines up with hint 2.
- `decrypt` applies `unshift` across the whole ciphertext, cycling through the key character-by-character (`key[i % len(key)]`), which is standard Vigenère key-repetition.

Since the key wasn't known, `solve.py` just brute-forces every single-character key from the 16-letter alphabet, decrypts with it, and only prints results where the intermediate decrypted string is valid `ALPHABET` characters *and* the final base16-decoded output is printable — filtering out garbage automatically:

```bash
python solve.py
```
```
Key: a, Plaintext: TcNcd.N&&'%%R% 
Key: p, Plaintext: et_tu?_77866c61
```

Two candidates passed the printable-character filter, but `Key: a` is clearly noise (`TcNcd.N&&'%%R%`), while `Key: p` decodes to clean readable text: `et_tu?_77866c61`.

## Flag
```
picoCTF{et_tu?_77866c61}
```