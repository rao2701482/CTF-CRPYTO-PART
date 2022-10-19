url编码特点:

% 拼接上16进制数(ascii字符)

可以直接把url编码的内容直接在浏览器栏中进行解码

空格在浏览器栏中解码为%20, 而+在url编码中代表空格.

![url编码](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/url%E7%BC%96%E7%A0%81.png)

---

ctf-wscan: ctf比赛的扫描工具
dirsearch: 真实渗透中的扫描工具(强大一些)

--- 

php首页源码查看文件: index.phps

----

## 例题1

![phps源码](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/phps%E6%BA%90%E7%A0%81.png)

![参数](https://github.com/rao2701482/CTF-CRPYTO-PART/blob/main/%E5%9B%BE%E7%89%87%E8%B5%84%E6%96%99/%E5%8F%82%E6%95%B0.png)

=> 要的内容是编码后的admin作为id的参数值
=> 本来我想的是拦截之后, 通过主动对admin进行url编码发送
=> 但是老师的办法是利用浏览器只会对url编码进行一次解码, 从而对admin进行两次url的编码, 从而满足题目条件
