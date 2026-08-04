# Insp3ct0r

## Challenge
Web Exploitation, Easy. Inspect the code at `http://fickle-tempest.picoctf.net:61890`.

## Hints
1. How do you inspect web code on a browser?
2. There's 3 parts

## Solution
Inspected the page HTML source, found the first part of the flag in a comment:

```html
<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->
```

Analyzed the CSS file, found the second part of the flag:

```css
t3ct1ve_0r_ju5t
```

Inspected the JavaScript code, found the final part of the flag:

```js
_lucky?302945a7}
```

Concatenated all three parts to form the complete flag.

## Flag
```
picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?302945a7}
```