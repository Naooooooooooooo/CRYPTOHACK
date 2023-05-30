# XOR STARTER
The challenge told us to xor each character in the string `label` with `13` to get the flag

To xor the character, first we need to convert it into integer using `ord()` function then after doing xor with `13` we use `chr()` function to convert it back to string

We loop through all character:
```py
xor_str = ''.join(chr(ord(c) ^ 13) for c in 'label')
```
The output:
>aloha

So our flag is:
>crypto{aloha}
