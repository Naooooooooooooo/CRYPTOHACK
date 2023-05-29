# HEX
The challenge gives us a flag encoded by hex
>63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d

So we just need to convert it

The function `bytes.hex()` in python can be used to convert hex to bytes.

```py
print(bytes.hex('63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d'))
```
The flag:
>crypto{You_will_be_working_with_hex_strings_a_lot}
