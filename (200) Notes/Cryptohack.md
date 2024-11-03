- string to numbers(take the ordinal bytes of the message, convert them into hexadecimal, and concatenate)
```
message: HELLO  
ascii bytes: [72, 69, 76, 76, 79]  
hex bytes: [0x48, 0x45, 0x4c, 0x4c, 0x4f]  
base-16: 0x48454c4c4f  
base-10: 310400273487
```

```python
a = ''
for ch in 'label':
...     a += chr(ord(ch) ^ 13)
```
