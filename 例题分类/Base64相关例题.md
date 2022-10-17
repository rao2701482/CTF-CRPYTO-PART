概念
正常的编码, 是把字符编码为二进制数
但base64是把二进制数编码为字符(编解码概念相反)

组成: 由64个最常用的ascii符合,大小写字母各26个、10个数字、加号+、斜杠/, =作为后缀填充(编码后的字符数应为4的倍数)

作用: 把非ascii字符都转化为ascii字符, 兼容旧的只能只有ascii的系统

base64编码示例: 有自己的码表 
![base64编码示例](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E7%BC%96%E7%A0%81%E7%A4%BA%E4%BE%8B.png)

base64编码的特征: 
![base64编码的特征](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E5%85%B3%E9%94%AE%E7%89%B9%E5%BE%81.png)

linux和python进行base64编解码的方式: 
![编码方式](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/base64%E7%BC%96%E8%A7%A3%E7%A0%81.png)
