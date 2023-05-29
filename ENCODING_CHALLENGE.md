# ENCODING CHALLENGE
The source code for the server is in [13377.py]("https://cryptohack.org/static/challenges/13377_43de0a0efed6ed7bd890d1c79db22fb1.py") 

We connect to server using `nc socket.cryptohack.org 13377`

Connecting then i receive a json format:
>{"type": "bigint", "encoded": "0x6d656d6f5f6d657461646174615f696e7465677261746564"}

Then it requires an input in json format from user

Looking at the source code:
```py
encoding = random.choice(ENCODINGS)
```
```py
ENCODINGS = [
    "base64",
    "hex",
    "rot13",
    "bigint",
    "utf-8",
]
```
Firstly, it choose an encoding type in random
```py
if encoding == "base64":
            encoded = base64.b64encode(self.challenge_words.encode()).decode() # wow so encode
        elif encoding == "hex":
            encoded = self.challenge_words.encode().hex()
        elif encoding == "rot13":
            encoded = codecs.encode(self.challenge_words, 'rot_13')
        elif encoding == "bigint":
            encoded = hex(bytes_to_long(self.challenge_words.encode()))
        elif encoding == "utf-8":
            encoded = [ord(b) for b in self.challenge_words]
```
Then encode the `self.challenge_words` with `challenge_words` is a random string from `/usr/share/dict/words` file
```py
with open('/usr/share/dict/words') as f:
    WORDS = [line.strip().replace("'", "") for line in f.readlines()]
```
```py
self.challenge_words = "_".join(random.choices(WORDS, k=3))
```
Encoding it then send to the client

The `challenge()` function handles our input
```py
def challenge(self, your_input):
        if self.stage == 0:
            return self.create_level()
        elif self.stage == 100:
            self.exit = True
            return {"flag": FLAG}

        if self.challenge_words == your_input["decoded"]:
            return self.create_level()

        return {"error": "Decoding fail"}
```
To get the flag, the `self.stage` variable has to be 100

In the `create_level()` we see that
```py
self.stage += 1
```
So the server has to run `create_level()` 100 times
And to trigger that, we have to meet the condition
```py
if self.challenge_words == your_input["decoded"]:
            return self.create_level()
```

We need to send the json format that looks like
>{"encoded": ...}

`...` is the decoded string of `challenge_words` sent by server

Here's the script:
```py
from pwn import *
import json
import base64
from Crypto.Util.number import *
import codecs
def bigint_decode(a):
    return long_to_bytes(int(a,16)).decode('utf-8')
def hex_decode(a):
    return bytes.fromhex(a).decode('utf-8')
def utf8_decode(a):
    b = ''
    for i in a:
        b += chr(i)
    return b
rm = remote('socket.cryptohack.org', 13377)
for i in range(100):
    bytes_recv = rm.recv(1024)
    str_from_bytes = bytes_recv.decode('utf-8')[0:-1]
    print(str_from_bytes)
    json_data = json.loads(str_from_bytes)
    if json_data['type'] == 'base64':
        json_to_send = json.dumps({"decoded": base64.b64decode(json_data['encoded']).decode('utf-8')})
    elif json_data['type'] == 'bigint':
        json_to_send = json.dumps({"decoded": bigint_decode(json_data['encoded'])})
    elif json_data['type'] == 'rot13':
        json_to_send = json.dumps({"decoded": codecs.decode(json_data['encoded'],'rot13')})
    elif json_data['type'] == 'hex':
        json_to_send = json.dumps({"decoded": hex_decode(json_data['encoded'])})
    else:
        json_to_send = json.dumps({"decoded": utf8_decode(json_data['encoded'])})
    rm.sendline(json_to_send)
print(rm.recv(1024).decode('utf-8'))
```
The output:
```
{"type": "base64", "encoded": "Z3Jhdml0eV93b3JyaWVkX3Bvd2Rlcg=="}
{"type": "utf-8", "encoded": [98, 117, 100, 103, 101, 116, 115, 95, 97, 99, 99, 111, 114, 100, 105, 110, 103, 108, 121, 95, 115, 116, 97, 102, 102]}
{"type": "base64", "encoded": "bGFzZXJfcGFydGljaXBhbnRzX3ZhdGljYW4="}
.
.
.

{"flag": "crypto{3nc0d3_d3c0d3_3nc0d3}"}
```

Flag:
>crypto{3nc0d3_d3c0d3_3nc0d3}
