# Mind your P's and Q's


## Challenge
In RSA, a small e value can be problematic, but what about N? Can you decrypt this?
values

## Hints
1. Bits are expensive, I used only a little bit over 100 to save money

## Solution

1. The challenge gives an RSA modulus `N` and hints that it's built from primes only a bit over 100 bits each, meaning `N` is small enough to be factored by a lookup service rather than needing to brute-force factor it manually. So the modulus was looked up on `factordb`:

948406957756830799684818171639547165784816468744946013083947881743680617123566349

This factoring returned the two prime factors:
1891771437429478964908181306574287207137
501332739776173570344039681219489434626477

2. With the primes `p` and `q` recovered, along with the ciphertext `c`, modulus `n`, and public exponent `e = 65537`, a standard RSA decryption script (`solve.py`) was written to compute Euler's totient `phi = (p-1)*(q-1)`, derive the private exponent `d` via modular inverse of `e` mod `phi`, and decrypt the ciphertext `c` using `m = c^d mod n`.

```python
    from Crypto.Util.number import inverse, long_to_bytes


    c = 15341890103764929939105506004034128738090325640037083301857608662849501626260517
    n = 948406957756830799684818171639547165784816468744946013083947881743680617123566349
    e = 65537

    p = 1891771437429478964908181306574287207137
    q = 501332739776173570344039681219489434626477

    phi=(p-1)*(q-1)


    d=inverse(e,phi)

    m=pow(c,d,n)

    print(long_to_bytes(m)[::-1])
```

3. Running the script converted the decrypted integer `m` back into bytes and reversed the byte order, revealing the flag.

## Flag
```
picoCTF{sm11_N_n0_goo_d1cd7ae91}
```