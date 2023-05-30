# You either know, XOR you don't

The challenge give us the encrypted flag

>0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104

That encrypted hex has length `84` so the flag has `42` characters because one hex takes 4 bits

The hint to find the key is the flag format which looks like
 >crypto{...}

 So i just brute force all single byte and check if the result has some character of the format

 ```py
 a = '0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104'
a = bytes.fromhex(a)
flag_form = b'crypto{}'
count = 0
b = [i for i in flag_form]
for i in range(256):
    c = bytes(i ^ j for j in a)
    if c[0]==b[0] or c[1]==b[1] or c[2] == b[2] or c[3]==b[3] or c[4]==b[4] or c[5]==b[5] or c[6]==b[6] or c[-1]==b[-1]:
        print(i, end=' ')
        print(c)

 ```

 And i have the output

 ```
 79 b'ADnpiKQ\x07Din0h{aX\x12AHEs\x14_qjin0h{aX\x12AH1i{\x1eZNK'
82 b'\\YsmtVL\x1aYts-uf|E\x0f\\UXn\tBlwts-uf|E\x0f\\U,tf\x03GSV'
88 b"VSyg~\\F\x10S~y'\x7flvO\x05V_Rd\x03Hf}~y'\x7flvO\x05V_&~l\tMY\\"
101 b'knDZCa{-nCD\x1aBQKr8kboY>u[@CD\x1aBQKr8kb\x1bCQ4pda'
107 b'e`JTMou#`MJ\x14L_E|6elaW0{UNMJ\x14L_E|6el\x15M_:~jo'
109 b'cfLRKis%fKL\x12JYCz0cjgQ6}SHKL\x12JYCz0cj\x13KY<xli'
121 b'wrXF_}g1r_X\x06^MWn$w~sE"iG\\_X\x06^MWn$w~\x07_M(lx}'
 ```

So our key will look like

>1 |2 |3 |4 |5 |6 |7 |8 |9 |10|11|12|13|14|15|16|17|18|19|20|21|22|23|24|25|26|27|28|29|30|31|32|33|34|35|36|37|38|39|40|41|42|
6d|79|58|4f|52|6b|65|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |79|



I have no clue about the other bytes of the key

Then i see that the ascii value of those numbers are all character, so i convert it and see that

>myXORke**********************************y

I just guest it's a loop then i try the key
>myXORkeymyXORkeymyXORkeymyXORkeymyXORkeymy

It has the last character `y` so it might be right

XOR it
```py
a = '0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104'
a = bytes.fromhex(a)
xor_list = [0x6d, 0x79, 0x58, 0x4f, 0x52, 0x6b, 0x65, 0x79]
byte_list = []
count = 0
print(len(a))
for i in range(42):
    byte_list.append(a[i] ^ xor_list[count])
    count = (count + 1) % 8
print(''.join(chr(c) for c in byte_list))
```

Then the result:
>crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}
