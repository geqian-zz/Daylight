---
{"aliases":null,"tags":["1_AtomNote"],"number headings":"auto, first-level 1, max 6, A.1.","Created-Date":"2023-09-24 10:28:34","Modified-Date":"2023-09-24 10:31:16","dg-publish":true,"permalink":"/A02_Code/A021_C/C_malloc函数/","dgPassFrontmatter":true}
---




# A. 函数使用基本说明


## A.1. 函数原型

```c
p = (int *) malloc(n*sizeof(int));


```



## A.2. 函数返回值
malloc 函数返回的实际是一个 **无类型指针**，必须在其前面加上指针类型强制转换才可以使用。

如果分配成功，则返回指向被分配内存的指针，否则返回空指针 NULL。



