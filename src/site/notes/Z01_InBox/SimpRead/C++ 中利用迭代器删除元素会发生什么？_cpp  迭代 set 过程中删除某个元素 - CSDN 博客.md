---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://blog.csdn.net/YF_Li123/article/details/75003425","title":"C++ 中利用迭代器删除元素会发生什么？_cpp  迭代 set 过程中删除某个元素 - CSDN 博客","summary":null,"Created-Date":"2024-01-12 19:54:15","Modified-Date":"2024-04-18 11:52:12","permalink":"/Z01_InBox/SimpRead/C++ 中利用迭代器删除元素会发生什么？_cpp  迭代 set 过程中删除某个元素 - CSDN 博客/","dgPassFrontmatter":true}
---

**C++ 中利用迭代器删除元素会发生什么？**

（1）对于关联容器（如 map，set，multimap，multiset），删除当前的 iterator，仅仅会使当前的 iterator 失效，只要在 erase 时，递增当前的 iterator 即可。这是因为 map 之类的容器，使用了红黑树来实现，插入，删除一个结点不会对其他结点造成影响。使用方式如下例子：

```cpp
set<int> valset = { 1,2,3,4,5,6 };
set<int>::iterator iter;
for (iter = valset.begin(); iter != valset.end(); )
{
     if (3 == *iter)
          valset.erase(iter++);
     else
          ++iter;
}
```

因为传给 erase 的是 iter 的一个副本，iter++ 是下一个有效的迭代器。

（2）对于序列式容器（如 vector，deque 等），删除当前的 [iterator](https://so.csdn.net/so/search?q=iterator&spm=1001.2101.3001.7020) 会使后面所有元素的 iterator 都失效。这是因为 vector，deque 使用了连续分配的内存，删除一个元素导致后面所有的元素会向前移动一个位置。不过 erase 方法可以返回下一个有效的 iterator。使用方式如下, 例如：

```cpp
vector<int> val = { 1,2,3,4,5,6 };
vector<int>::iterator iter;
for (iter = val.begin(); iter != val.end(); )
{
     if (3 == *iter)
          iter = val.erase(iter);     //返回下一个有效的迭代器，无需+1
     else
          ++iter;
}
```



**补充：**

STL 中的容器按存储方式分为两类：一类是序列容器（如：vector，deque），另一类是关联容器（如：list，map，set）。

在使用 erase 方法删除元素时，有几点需要注意：

1） 对于关联容器（如 map， set，multimap，multiset），删除当前的 iterator，仅仅会使当前的 iterator 失效，只要在 erase 时，递增当前 iterator 即可。这是因为 map 之类的容器，使用了 [红黑树](https://so.csdn.net/so/search?q=%E7%BA%A2%E9%BB%91%E6%A0%91&spm=1001.2101.3001.7020) 来实现，插入、删除一个结点不会对其他结点造成影响。

2）对于序列式容器（如 vector，deque），删除当前的 iterator 会使后面所有元素的 iterator 都失效。这是因为 vetor，deque 使用了连续分配的内存，删除一个元素导致后面所有的元素会向前移动一个位置。还好 erase 方法可以返回下一个有效的 iterator。

3）对于 list 来说，它使用了不连续分配的内存，并且它的 erase 方法也会返回下一个有效的 iterator，因此上面两种正确的方法都可以使用。




---
- [[A02_Code/A027_C++/STL\|STL]]