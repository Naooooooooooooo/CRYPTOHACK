# BASE64
The challenge gives us a hex string
>72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf

To get the flag we first need to decode it into bytes and then encode it into Base64

To decode it into bytes we use `bytes.fromhex()` function
```py
bytes.fromhex('72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf')
```
To encode it into base64 we need to import `base64` module
```py
import base64
```
Then we use function `base64.b64encode()` to encode

Full script:
```py
import base64
a = '72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf'
decoded_bytes = bytes.fromhex(a)
print(base64.b64encode(decoded_bytes))
```
And we get the flag:
>crypto/Base+64+Encoding+is+Web+Safe/
