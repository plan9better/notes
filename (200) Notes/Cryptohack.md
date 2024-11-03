## string to numbers(take the ordinal bytes of the message, convert them into hexadecimal, and concatenate)
```
message: HELLO  
ascii bytes: [72, 69, 76, 76, 79]  
hex bytes: [0x48, 0x45, 0x4c, 0x4c, 0x4f]  
base-16: 0x48454c4c4f  
base-10: 310400273487
```
`pip install pycryptodome`
```python
from Crypto.Util.number import *
msg = 'hello from the other side'
n = bytes_to_long(msg)
msg = long_to_bytes(n)
```
## XOR (We can XOR integers by first converting the integer from decimal to binary)
```python
a = ''
for ch in 'label':
...     a += chr(ord(ch) ^ 13)
# or
# pip install pwntools
from pwn import xor

ciphertext = "5d41402abc4b2a76b9719d911017c592"
key = "secret"

xored = xor(bytes.fromhex(ciphertext), key.encode())

```
