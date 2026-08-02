# mod26

## Challenge

Cryptography can be easy, do you know what `ROT13` is? File provided: `values.txt`.

## Hints

1. This can be solved online if you don't want to do it by hand.

## Solution

```bash
cat values.txt
```

```text
cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_45559noq}
```

Ran it through `tr` to apply `ROT13`:

```bash
echo "cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_45559noq}" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

## Flag

```text
picoCTF{next_time_I'll_try_2_rounds_of_rot13_45559abd}
```