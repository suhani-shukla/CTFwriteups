# Super SSH

## Challenge

Using a Secure Shell (`SSH`) is going to be pretty important. `ssh` as `ctf-player` to `titan.picoctf.net` at port `52911` to get the flag. Password: `1db87a14`. Accept the fingerprint with `yes` if asked.

## Hints

1. https://linux.die.net/man/1/ssh
2. You can try logging in `as` someone with `<user>@titan.picoctf.net`
3. How could you specify the port?
4. Remember, passwords are hidden when typed into the shell

## Solution

```bash
ssh ctf-player@titan.picoctf.net -p 52911
```

Typed `yes` to accept the fingerprint, entered the password, got the flag.

## Flag

```text
picoCTF{s3cur3_c0nn3ct10n_45a48857}
```