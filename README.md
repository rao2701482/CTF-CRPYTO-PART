# CTF-CRPYTO-PART
加密相关例题的学习过程记录分享

分析密文的的思路:

# 判断进制
1. 是否值最大为7, 则为八进制编码 => 转ascii处理
2. 最大127, 则为10进制 => 转ascii处理
3. x  数字0-9 a-f,  则为16进制数

# 判断编码:
1. unicode: \u002c    
(

=> \U[Hex]  \U+[Hex]   => 直接chr(int('002c', 16))解就好, 本身python3就是unicode编码

=> &$x[Hex]; &#[Dec];  => 放html打开
)

2. base64 家族
3. url编码              => 直接放浏览器输入栏中

# 判断加密
 
(单表替换加密)

1. 摩斯密码 => 密码表
2. 凯撒密码 => 正常选择, ROT-13, 变异凯撒(分析映射), 词频分析(工具软件)
3. 培根加密 => 密码表

(多表替换加密)
1. 维吉尼亚密码 => 会给密文 和 秘钥

# 分组

1. 栅栏加密

# hash

1. MD5

----

技巧

1. 图片文件可以下载下来, 然后用strings 去打开看内容, 一般末尾会有特别的值
2. 网站题, 看html源码, 看请求响应的响应头, 注意会话信息
3. 右键文件的属性可能会有一些信息
