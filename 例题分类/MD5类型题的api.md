python hashlib模块和itertools

```
import hashlib
m = hashlib.md5()
m.update('hello'.encode())
m.hexdigest()


import itertools
a =b =c=d ='0123456789'
s = itertools(a,b,c,d)
for i in s:
    print(''.join(i))
```


一般都是给一个字符串, 中间缺几个字符,  然后让补上字符, 然后对比对应的MD5值, 一样的话, 则补的值正确
