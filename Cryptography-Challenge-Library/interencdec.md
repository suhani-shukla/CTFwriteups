# interencdec

## Challenge
Misc/crypto challenge — a file that needs multiple rounds of decoding chained together to reach the real flag.

## Hints
1. Engaging in various decoding processes is of utmost importance.

## Solution
Checked the file type:

```bash
file enc_flag
```
```
enc_flag: ASCII text
```

Dumped it:

```bash
cat enc_flag
```
```
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyMHdNakV5TnpVNGZRPT0nCg==
```

Looks like base64. Decoded it:

```bash
echo "YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyMHdNakV5TnpVNGZRPT0nCg==" | base64 -d
```
```
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fQ=='
```

That output is itself a Python bytes-literal wrapping another base64 string (`b'...'`). Stripped the wrapper and decoded again:

```bash
echo "d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fQ==" | base64 -d
```
```
wpjvJAM{jhlzhy_k3jy9wa3k_m0212758}
```

That's now a `JAM{...}`-wrapped string that looks Caesar-shifted, similar structure to a `picoCTF{...}` flag. Brute-forced all 26 shifts:

```bash
for i in {0..25}; do echo "Shift $i: $(echo 'wpjvJAM{jhlzhy_k3jy9wa3k_m0212758}' | python3 -c "import sys; s=$i; print(''.join(chr((ord(c)-97-s)%26+97) if 'a'<=c<='z' else c for c in sys.stdin.read()))")"; done
```
```
Shift 0: wpjvJAM{jhlzhy_k3jy9wa3k_m0212758}
Shift 1: voiuJAM{igkygx_j3ix9vz3j_l0212758}
Shift 2: unhtJAM{hfjxfw_i3hw9uy3i_k0212758}
Shift 3: tmgsJAM{geiwev_h3gv9tx3h_j0212758}
Shift 4: slfrJAM{fdhvdu_g3fu9sw3g_i0212758}
Shift 5: rkeqJAM{ecguct_f3et9rv3f_h0212758}
Shift 6: qjdpJAM{dbftbs_e3ds9qu3e_g0212758}
Shift 7: picoJAM{caesar_d3cr9pt3d_f0212758}
Shift 8: ohbnJAM{bzdrzq_c3bq9os3c_e0212758}
Shift 9: ngamJAM{aycqyp_b3ap9nr3b_d0212758}
Shift 10: mfzlJAM{zxbpxo_a3zo9mq3a_c0212758}
Shift 11: leykJAM{ywaown_z3yn9lp3z_b0212758}
Shift 12: kdxjJAM{xvznvm_y3xm9ko3y_a0212758}
Shift 13: jcwiJAM{wuymul_x3wl9jn3x_z0212758}
Shift 14: ibvhJAM{vtxltk_w3vk9im3w_y0212758}
Shift 15: haugJAM{uswksj_v3uj9hl3v_x0212758}
Shift 16: gztfJAM{trvjri_u3ti9gk3u_w0212758}
Shift 17: fyseJAM{squiqh_t3sh9fj3t_v0212758}
Shift 18: exrdJAM{rpthpg_s3rg9ei3s_u0212758}
Shift 19: dwqcJAM{qosgof_r3qf9dh3r_t0212758}
Shift 20: cvpbJAM{pnrfne_q3pe9cg3q_s0212758}
Shift 21: buoaJAM{omqemd_p3od9bf3p_r0212758}
Shift 22: atnzJAM{nlpdlc_o3nc9ae3o_q0212758}
Shift 23: zsmyJAM{mkockb_n3mb9zd3n_p0212758}
Shift 24: yrlxJAM{ljnbja_m3la9yc3m_o0212758}
Shift 25: xqkwJAM{kimaiz_l3kz9xb3l_n0212758}
```

`Shift 7` is the one that reads real: `caesar_d3cr9pt3d`. Wrapper's still `picoJAM{` on that line since the script only shifts lowercase letters, but the plaintext content is clearly the flag with a mangled `JAM` prefix instead of `CTF`.

## Flag
```
picoCTF{caesar_d3cr9pt3d_f0212758}
```