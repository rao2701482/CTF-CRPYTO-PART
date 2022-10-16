### 基础例题1

![基础例题1]([https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/1.png](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%9F%BA%E7%A1%80%E4%BE%8B%E9%A2%981.png))

这是最基本的题型, 考察如何从二进制中获取目标的flag

需要的前置知识:
1. ascii的可见字符范围: 32~127
2. python语法: int('目标字符串', 目标字符串的进制数) => 返回10进制  eg: int('A', 16) => 10
3. python语法: chr(ascii)  => 返回ascii对应的字符编码            eg: chr(65)      => A
4. 了解各个进制的字符表示: 2进制 0b开头;  8进制 0o开头; 10进制 0d开头; 16进制 0x开头 (可以省略0, 或者会将0替换为\)

了解完这些后, 便能解这道题了
![基础例题答案](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%9F%BA%E7%A1%80%E4%BE%8B%E9%A2%981%E7%AD%94%E6%A1%88.png)
