## 基础例题1

![基础例题1](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%9F%BA%E7%A1%80%E4%BE%8B%E9%A2%981.png)

这是最基本的题型, 考察如何从二进制中获取目标的flag

需要的前置知识:
1. ascii的可见字符范围: 32~127
2. python语法: int('目标字符串', 目标字符串的进制数) => 返回10进制  eg: int('A', 16) => 10
3. python语法: chr(ascii)  => 返回ascii对应的字符编码            eg: chr(65)      => A
4. 了解各个进制的字符表示: 2进制 0b开头;  8进制 0o开头; 10进制 0d开头; 16进制 0x开头 (可以省略0, 或者会将0替换为\)

了解完这些后, 便能解这道题了

考察点: 如何进行2进制转换为ascii码

![基础例题答案](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%9F%BA%E7%A1%80%E4%BE%8B%E9%A2%981%E7%AD%94%E6%A1%88.png)


## 基础例题2
![基础例题2](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%9F%BA%E7%A1%80%E4%BE%8B%E9%A2%982.png)

考察点: 如何进行2,8,10,16进制转换为ascii码

![基础例题2答案](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%9F%BA%E7%A1%80%E4%BE%8B%E9%A2%982%E8%A7%A3%E7%AD%94.png)


## 基础例题3
![基础例题3](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%9F%BA%E7%A1%80%E4%BE%8B%E9%A2%983.png)

考察点: 
1. 已知ascii是7位二进制数, 最高位为0这个知识点.
2. 字符范围基本为0-9 a-f, 则简单判断为16进制
3. 变化点: 把两个16进制字符转化为10进制后发现, 字符范围超过了 ascii可见范围的32~127, 打印二进制后可发现最高位全部被置1
![基础例题3分析](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%9F%BA%E7%A1%80%E4%BE%8B%E9%A2%983%E5%88%86%E6%9E%90.png)
4. 因此试探性的主动把最高位的1转换为0, 即主动扣减128

![基础例题3答案](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%9F%BA%E7%A1%80%E4%BE%8B%E9%A2%983%E4%B8%BB%E5%8A%A8%E6%89%A3%E5%87%8F128.png)


## 基础例题4
![基础例题4](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/js%E9%A2%98%E7%9B%AE.png)
![基础例题4js](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/js2%E9%A2%98%E7%9B%AE.png)

考察点: 
1. 分析能力: 本身题目名称为simple_js, 所以需要主动去看js的代码, 但是代码中dechiffre()函数明细十分复杂不像是题目说的简单类型
2. 找到函数的调用处: 一个为用户侧的主动输入, 一个是图片蓝色处的主动硬编码的地方, 因此从这串字符中找突破口
3. 从前置知识点可知 '\x35' 属于16进制编码的一类, 因此作为16进行编码进行解答
4. '\x35' 这样的编码, 可以在python中直接由字符串转换为10进制的数值类型

![基础例题4](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/js%E7%AD%94%E6%A1%88.png)


## 进阶例题1
![进阶例题1](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E9%BB%91%E7%99%BD%E5%9B%BE%E7%89%87-%E9%A2%98%E7%9B%AE.png)

考察点:
1. 由黑色与白色的图片中可以得知, 非常类型二进制中的0和1
2. 在如何读取图片信息转化为01字符序列时, 可以使用python的pillow模块, 对图片进行处理
```
from PIL import Image
im = Image.open('文件')
dir(im)  => 查看文件的方法
im.getcolors() => 获得每个三原色的像素点数量
```
![进阶例题1分析](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E9%BB%91%E7%99%BD%E5%9B%BE%E7%89%87%E5%88%86%E6%9E%90.png)
3. 第二张图片为黑色图片, 我们查看到其有46656个像素点, 并且每个像素点的rgb三原色都为255, 则我们可以认为取三原色中的一个数值255来判断一张图片是否为黑色

![进阶例题1解答](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E9%BB%91%E7%99%BD%E5%9B%BE%E7%89%87-%E8%A7%A3%E7%AD%94.png)


## 进阶例题2
![进阶例题2](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E7%BA%A2%E7%BB%BF%E7%81%AFgif.mov)



