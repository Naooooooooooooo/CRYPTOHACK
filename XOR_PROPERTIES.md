# XOR PROPERTIES
We have some properties of `xor` operator
```
Commutative: A ⊕ B = B ⊕ A
Associative: A ⊕ (B ⊕ C) = (A ⊕ B) ⊕ C
Identity: A ⊕ 0 = A
Self-Inverse: A ⊕ A = 0
```

From that we have
> A ^ B ^ B = A ^ (B ^ B) = A ^ 0 = A

That means doing xor twice with the same number does not change the original number

The chalenge give us some keys and some xored keys with the flag

```
KEY1 = a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313
KEY2 ^ KEY1 = 37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e
KEY2 ^ KEY3 = c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1
FLAG ^ KEY1 ^ KEY3 ^ KEY2 = 04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf
```

We can retrieve the key and the flag by doing xor with the same number

>KEY2 ^ KEY1 ^ KEY1 = KEY2

Script:

```py
KEY1 = 0xa6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313
KEY2_xor_KEY1 = 0x37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e
KEY2 = KEY1 ^ KEY2_xor_KEY1 #KEY2 ^ KEY1 ^ KEY1 = KEY2
KEY2_xor_KEY3 = 0xc1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1
KEY3 = KEY2_xor_KEY3 ^ KEY2 # KEY3 ^ KEY2 ^ KEY2 = LEY3
#FLAG ^ KEY1 ^ KEY3 ^ KEY2 = 04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf
FLAG = 0x04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf ^ KEY1 ^ KEY2_xor_KEY3
byte_length = (FLAG.bit_length() + 7) // 8 #calculate the no of bytes the FLAG takes
print(FLAG.to_bytes(byte_length, byteorder='big'))
```

Because it's in hex format so the need to prefix it with `0x`

Then we get the flag:
>crypto{x0r_i5_ass0c1at1v3}
