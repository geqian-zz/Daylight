---
{"dg-publish":true,"permalink":"/A02_Code/A021_C/C_malloc函数/","tags":["1_AtomNote"]}
---




# A. 函数使用基本说明


## A.1. 函数原型

```c
p = (int *) malloc(n*sizeof(int));


```



## A.2. 函数返回值
malloc 函数返回的实际是一个 **无类型指针**，必须在其前面加上指针类型强制转换才可以使用。

如果分配成功，则返回指向被分配内存的指针，否则返回空指针 NULL。



