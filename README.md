# ASCII
The challenge gives a list containing the ascii numbers
>[99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]

We can use the `chr()` function in python to convert the ascii number to character

Example:
```py
chr(65)
```
Return 'A' which is the corresponding character with 65 in ascii table

We loop through the list and get the flag:
```py
a = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
b = ''
for i in a:
    b += chr(i)
print(b)
```
Flag:
>crypto{ASCII_pr1nt4bl3}
