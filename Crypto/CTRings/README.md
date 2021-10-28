#Challenge description

**msg = 'this message and the flag are encrypted with AES-CTR'
encrypted_msg = '7a35feb81c72621b35418da53b743687663f5531cdc29f055b15669cc2afbc48c2d00a05821b86123b484fab084e02a9b97a4480'
encrypted_flag = '7d35f2a75072661c235391834f4707972e78622298c89d574e01658294d0ed15f2fd1e45924d9f'**




## Solution

So the challenge here is to find the encrypted flag having a message and its cipher.Since this is an AES with CTR mode the idea is to xor the message with the encrypted message to obtain the ke, then xor the obtained key with the encrypted flag. 
We can automate this task with a simple python script

``` Python
from challenge import *
from pwn import xor


key = xor(bytes.fromhex(encrypted_msg),msg.encode())

flag = xor(key,bytes.fromhex(encrypted_flag))

print(flag)

'''

flag : shellmates{CTR_th3_vuln3r4bl3_43S_m0d3}
