---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://blog.csdn.net/qq_42445148/article/details/111168089","title":"C 语言：结构体中（.）和（-＞）的区别_结构体. 和→的区别_真的那么难吗？的博客 - CSDN 博客","summary":null,"Created-Date":"2023-09-24 10:42:04","Modified-Date":"2024-04-18 11:52:12","permalink":"/Z01_InBox/SimpRead/C 语言：结构体中（_）和（-＞）的区别_结构体_ 和→的区别_真的那么难吗？的博客 - CSDN 博客/","dgPassFrontmatter":true}
---

### Z.1.1. 首先，要了解

（*a）.b 等价于 a->b。

### Z.1.2. 概念上：

一般情况下用 “.”，只需要声明一个 [结构体](https://so.csdn.net/so/search?q=%E7%BB%93%E6%9E%84%E4%BD%93&spm=1001.2101.3001.7020)。格式是，结构体类型名 + 结构体名。然后用结构体名加 “.” 加域名就可以引用域 了。因为自动分配了结构体的内存。如同 int a; 一样。

而用 “->”，则要声明一个结构体的指针，还要手动开辟一个该结构体的 [内存](https://so.csdn.net/so/search?q=%E5%86%85%E5%AD%98&spm=1001.2101.3001.7020)，然后把返回的指针给声明的结构体指针，才能用 “->” 正确引用。否则内存中只分配了指针的内存，没有分配结构体的内存，导致想要的结构体实际上是不存在。这时候用 “->” 引用自然出错了，因为没有结构体，自然没有结构体的域了。

### Z.1.3. 二者的相同点:

两个都是二元操作符，其右操作符是成员的名称。

### Z.1.4. 二者的不同点

点操作符左边的操作数是一个 “结果为结构” 的表达式；  
箭头操作符左边的操作数是一个指向结构的指针。

![](https://img-blog.csdnimg.cn/20201214142350227.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNDQ1MTQ4,size_16,color_FFFFFF,t_70)

  
图中的画圈部分，表示两者意义相同