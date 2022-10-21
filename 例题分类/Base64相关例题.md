### 概念
正常的编码, 是把字符编码为二进制数
但base64是把二进制数编码为字符(编解码概念相反)

### 组成: 
由64个最常用的ascii符合,大小写字母各26个、10个数字、加号+、斜杠/, =作为后缀填充(编码后的字符数应为4的倍数)

### 作用: 
把非ascii字符都转化为ascii字符, 兼容旧的只能只有ascii的系统

### 码表:
![码表](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E7%BC%96%E7%A0%81%E8%A1%A8.png)


## base64编码示例: 有自己的码表 
![base64编码示例](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E7%BC%96%E7%A0%81%E7%A4%BA%E4%BE%8B.png)

## base64编码的特征: 字符与长度

![base64编码的特征](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E5%85%B3%E9%94%AE%E7%89%B9%E5%BE%81.png)

## linux和python进行base64编解码的方式: 
![编码方式](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E7%BC%96%E8%A7%A3%E7%A0%81.png)

-----

## 例题1

![base64例题1](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E4%BE%8B%E9%A2%981.png)

考察点:
考量字符特征: 最大为7. 联想8进制
=> 解码完后是base64的特征: 字符 + 长度

![base64例题1解答](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%85%AB%E8%BF%9B%E5%88%B6%E8%A7%A3%E6%9E%90%E5%AE%8C%E5%90%8E%E7%9A%84%E4%B8%AD%E9%97%B4%E7%BB%93%E6%9E%9C.png)

## 例题2

![base64例题2](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E4%BE%8B%E9%A2%982.png)

=> 当随意输入一个账号密码后, 弹出该错误提示, 根据经验, 说是该ip不行, 需要拦截并修改ip地址

=> 那使用burp suite软件进行proxy拦截, 然后再邮件repeat后再repeater模块 : 补上x-forwarded-for: 127.0.0.1进行伪造客户端ip进行 登录

![第二轮问题](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E7%AC%AC%E4%BA%8C%E8%BD%AE%E9%97%AE%E9%A2%98.png)

=> 说密码不对, 则去源码中找找结果

![源码中隐藏注释](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E6%BA%90%E7%A0%81%E4%B8%AD%E9%9A%90%E8%97%8F%E6%B3%A8%E9%87%8A.png)
=> 然后base64解码获得结果test123

=> 过关
![结果](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E7%BB%93%E6%9E%9C.png)

## 例题3

![混合编码](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E4%BE%8B%E9%A2%983%E6%B7%B7%E5%90%88%E7%BC%96%E7%A0%81.png)
![反复解码](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%8F%8D%E5%A4%8Dbase64%E8%A7%A3%E7%A0%81unicode%E8%A7%A3%E7%A0%81ascii%E8%A7%A3%E7%A0%81.png)

=> 就是按照字符特征进行反复解码

## 例题4

题目给出: exe文件
=> linux: file a.exe 分析文件类型为文本类型
=> 获得文本中的base64编码值(根据题目含义转化为图片)
=> 在线转换 or 放浏览器地址栏里 or ```<img src="xx">``` => 二维码扫描软件(QR search) 扫码后获得结果

## 例题5

考察点:
1. 打开源码看内容

![源码](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/js.png)
=> 得到提示: 说是要把我找到的内容作为margin的参数以post的方式提交到服务后台

2. 看响应头里是否有一些提示
![响应](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E4%BE%8B%E9%A2%981%E5%93%8D%E5%BA%94%E5%A4%B4.png)
=> 得到提示是flag: xxxxxx  看起来像base64编码

3. 提取编码作为结果
![提取](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/python%E8%84%9A%E6%9C%AC.png)
=> 这边有个小坑: 提取完的结果还需要进行一次base64解码

4. 我们发现每一次请求的响应头里的flag都不一样, 结合题目提示: 速度要快
=> 推理需要进行会话控制
![结果](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/python%E8%84%9A%E6%9C%AC2.png)


---
*Base家族*

![base家族特征](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base%E5%AE%B6%E6%97%8F.png)

- base16可以认为就是16进制编码, 以后16进制就直接用base16进行解码了
- base32可以观察是大写字节 + 没有01 和 89的字符串
- base85, emmmm  好复杂的样子....兜底试试

## 例题6: base32  base16解码
![简单例题](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base3216.png)

## 例题7: 脑洞: 键盘加密
![简单例题](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E9%94%AE%E7%9B%98%E5%8A%A0%E5%AF%86.png)

=> 沿着键盘顺序, 把目标字符包起来

## 例题8

考察点:
1. 分析字符规则, 发现是b85 b64 b16三类加密
2. 由于字符串很长, 我们一层层解码后发现: 是"b85 b64 b16"  ->  "b85 b64 b16"  -> "b85 b64 b16" 层层加密

![多层加密](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base%E8%BF%9E%E7%BB%AD%E8%A7%A3%E7%A0%81.png)

## 例题9: base家族混合连续解码

知识点: 为了避免以错误的编码方式解了正确编码方式的 字符串, 所以在解码的末尾使用 decode()进行把二进制解为字符, 如果能正确解为字符, 才认为进行了正确的解码

![base连续解码](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E4%BB%BB%E6%84%8F%E8%A7%A3%E7%A0%81.png)

## 例题10: 仿base64解码
=> 对自定义编码 按码表解码后转为 base64编码 => 对脚本的最终结果进行base64解码

![仿base64解码](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base%E7%BC%96%E7%A0%81.png)

---

base64编码:
1. 3个字符 => 24位二进制数 =>分隔为4组6位二进制数 => 编码为4个base64编码字符
2. 当只有一个字符时, 这个过程里的只有8位二进制数, 因此需要主动填充4位二进制数, 然后再补充等号
3. 当只有两个字符时, 只有16个二进制数, 与18位相比却两个, 需要主动填充2位二进制数, 然后补充等号
![编码1](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E7%BC%96%E7%A0%811.png)
![编码2](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/bsae64%E7%BC%96%E7%A0%812.png)

base64解码:
![看图](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E8%A7%A3%E7%A0%81%E4%B8%8E%E9%9A%90%E5%86%99.png)

隐写:
就是再base64解码的过程中, 在最后可以补的4个 or 2个二进制位做文章
题目特征: 会给非常多的base64编码字符串, 然后从中提取隐写的二进制位, 拼接后得到最终的flag


判断是否有隐写数据:
=> 只有末尾有等号, 才有隐写的内容, 一个等号隐写2位
=> 解码再编码, 然后对比是否一样, 如果不一样, 就说明有隐写信息

提取隐写信息: 
str.zfill(6)

## 例题11

![base64隐写题目](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E9%9A%90%E5%86%99%E9%A2%98%E7%9B%AE.png)

=> 脚本在做什么: 判断一行字符串是否有等号, 如果有等号则代表最后非等号的字母是有进行二进制位填充的, 一个等号填充2位, 两个等号填充4位
=> 我们先去除最后的等号, 然后对最后一个字母 从A-Za-z0-9+/这一串序列中, 去定位字符的index, 然后转化为二进制后, 提取补全的位数
=> 把所有位数提取拼接完毕后, 可以进行二进制的解码为 ascii, 尝试得到最终的flag


![base64隐写答案](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E9%9A%90%E5%86%99%E7%AD%94%E6%A1%88.png)




