# CTF-CRPYTO-PART
加密相关例题的学习过程记录分享

判断字符编码的注意点:

判断进制
1. 是否值最大为7, 则为八进制编码 => 转ascii处理
2. 最大127, 则为10进制 => 转ascii处理
3. x  数字0-9 a-f,  则为16进制数

判断编码:
1. unicode: \u002c    
(

=> \U[Hex]  \U+[Hex]   => 直接chr(int('002c', 16))解就好, 本身python3就是unicode编码

=> &$x[Hex]; &#[Dec];  => 放html打开
)

2. base64 家族
3. url编码              => 直接放浏览器输入栏中
