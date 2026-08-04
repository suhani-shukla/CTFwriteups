# where-are-the-robots

## Challenge
Web Exploitation, Easy. Find the robots at `http://fickle-tempest.picoctf.net:55198`.

## Hints
1. What part of the website could tell you where the creator doesn't want you to look?

## Solution
Appended `robots.txt` to the URL:

```
http://fickle-tempest.picoctf.net:55198/robots.txt
```

This returned a `Disallow` entry pointing to `cc6b1.html`. Navigated to that file to retrieve the flag:

```
http://fickle-tempest.picoctf.net:55198/cc6b1.html
```

## Flag
```
picoCTF{ca1cu1at1ng_Mach1n3s_cc6b1}
```