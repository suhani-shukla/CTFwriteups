# CTF Writeups

Personal collection of Capture The Flag (CTF) writeups — solutions, notes, and
commands from challenges I've solved. Mostly picoCTF for now, more to be
added as I go.

Each writeup documents the challenge description, any hints given, the exact
steps/commands used to solve it, and the resulting flag.

## Repo Structure

```
.
├── README.md
└── Beginners-Guide-Library/
    ├── warmedUp.md
    ├── 2warm.md
    ├── Bases.md
    ├── wave-a-flag.md
    ├── tab-tab-attack.md
    ├── strings-it.md
    └── first-grep.md
```

Folders are organized by category/series as they grow (e.g. `Beginners-Guide-Library`
for picoCTF's General Skills intro track). New categories get their own folder.

## Writeup Format

Every writeup follows the same structure:

```
# Challenge Name
## Challenge
Brief description of the challenge as given.
## Hints
Numbered list of hints provided (if any).
## Solution
Commands run and brief explanation of the approach.
## Flag
The captured flag.
```

## Index

### Beginners Guide Library (picoCTF — General Skills)

| # | Challenge | Tools/Concepts | Flag |
|---|---|---|---|
| 1 | [Warmed up](Beginners-Guide-Library/warmedUp.md) | `printf`, hex-to-decimal | `picoCTF{61}` |
| 2 | [2warm](Beginners-Guide-Library/2warm.md) | `bc`, decimal-to-binary | `picoCTF{101010}` |
| 3 | [Bases](Beginners-Guide-Library/Bases.md) | `base64` decode | `picoCTF{l3arn_th3_r0p35}` |
| 4 | [Wave a flag](Beginners-Guide-Library/wave-a-flag.md) | `chmod`, help flags (`-h`) | `picoCTF{b1scu1ts_4nd_gr4vy_ac5832c}` |
| 5 | [Tab, Tab, Attack](Beginners-Guide-Library/tab-tab-attack.md) | `unzip`, tabcomplete | `picoCTF{l3v3l_up!_t4k3_4_r35t!_fc588427}` |
| 6 | [strings it](Beginners-Guide-Library/strings-it.md) | `file`, `strings`, `grep` | `picoCTF{5tRIng5_1T_dB2CEA76}` |
| 7 | [First Grep](Beginners-Guide-Library/first-grep.md) | `strings`, `grep` | `picoCTF{grep_is_good_to_find_things_29f42460}` |

## Tools Referenced

`printf` · `bc` · `base64` · `chmod` · `unzip` · `file` · `strings` · `grep`

## Notes

- Flags are included in full for personal reference; redact before sharing publicly if needed.
- Writeups are added as challenges are solved — this index is updated alongside.