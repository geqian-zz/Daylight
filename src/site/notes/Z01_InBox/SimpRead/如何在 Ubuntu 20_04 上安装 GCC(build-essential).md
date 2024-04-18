---
{"dg-publish":true,"aliases":[null],"tags":[null],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://zhuanlan.zhihu.com/p/146205444","title":"如何在 Ubuntu 20.04 上安装 GCC(build-essential)","summary":null,"Created-Date":"2023-08-11 09:21:09","Modified-Date":"2024-04-18 11:52:10","permalink":"/Z01_InBox/SimpRead/如何在 Ubuntu 20_04 上安装 GCC(build-essential)/","dgPassFrontmatter":true}
---

本文最先发布在：

[如何在 Ubuntu 20.04 上安装 GCC(build-essential)](https://link.zhihu.com/?target=https%3A//www.itcoder.tech/posts/how-to-install-gcc-on-ubuntu-20-04/)

GNU 编译器集合是一系列用于语言开发的编译器和库的集合，包括: C, C++, Objective-C, Fortran, Ada, Go, and D 等编程语言。很多开源项目，包括 Linux kernel 和 GNU 工具，都是使用 GCC 进行编译的。

本文描述如何在 Ubuntu 20.04 上安装 GCC。

## Z.1. 一、在 Ubuntu 20.04 上安装 GCC

默认的 Ubuntu 软件源包含了一个软件包组，名称为 “build-essential”, 它包含了 GNU 编辑器集合，GNU 调试器，和其他编译软件所必需的开发库和工具。

想要安装开发工具软件包，以 拥有 sudo 权限用户身份或者 root 身份运行下面的命令：

```
sudo apt update
sudo apt install build-essential

```



这个命令将会安装一系列软件包，包括 `gcc`,`g++`, 和 `make`。

你可能还想安装关于如何使用 GNU/Linux 开发的手册。

```
sudo apt-get install manpages-dev

```

通过运行下面的命令，打印 GCC 版本，来验证 GCC 编译器是否被成功地安装。

```
gcc --version

```

在 Ubuntu 20.04 软件源中 GCC 的默认可用版本号为 `9.3.0`:

```
gcc (Ubuntu 9.3.0-10ubuntu2) 9.3.0
Copyright (C) 2019 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

就这些。GCC 已经在你的 Ubuntu 系统上安装好了，你可以开始使用它了。

## Z.2. 二、编译一个 Hello World 实例

使用 GCC 编译一个基本的 C 或者 C++ 程序非常简单。打开你的文本编辑器，并且创建下面的文件：

```
nano hello.c
#include <stdio.h>
int main()
{
  printf ("Hello World!\n");
  return 0;
}

```

保存文件，并且将它编译成可执行文件，运行：

```
gcc hello.c -o hello

```

这将在你运行命令的同一个目录下创建一个二进制文件，名称为 "hello”。

运行这个 `hell0` 程序：

```
./hello

```

程序应该打印：

```
Hello World!

```

## Z.3. 三、安装多个 GCC 版本

这一节提供一些指令，关于如何在 Ubuntu 20.04 上安装和使用多个版本的 GCC。更新的 GCC 编译器包含一些新函数以及优化改进。

在写作本文的时候，Ubuntu 源仓库包含几个 GCC 版本，从 `7.x.x` 到 `10.x.x`。在写作的同时，最新的版本是 `10.1.0`。

在下面的例子中，我们将会安装最新的三个版本 GCC 和 G++：

输入下面的命令，安装想要的 GCC 和 G++ ：

```
sudo apt install gcc-8 g++-8 gcc-9 g++-9 gcc-10 g++-10

```

下面的命令配置每一个版本，并且设置了优先级。默认的版本是拥有最高优先级的那个，在我们的场景中是 `gcc-10`。

```
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 100 --slave /usr/bin/g++ g++ /usr/bin/g++-10 --slave /usr/bin/gcov gcov /usr/bin/gcov-10
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 90 --slave /usr/bin/g++ g++ /usr/bin/g++-9 --slave /usr/bin/gcov gcov /usr/bin/gcov-9
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 80 --slave /usr/bin/g++ g++ /usr/bin/g++-8 --slave /usr/bin/gcov gcov /usr/bin/gcov-8

```

以后，如果你想修改默认的版本，使用 `update-alternatives` 命令：

```
sudo update-alternatives --config gcc

```

输出：

```
There are 3 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path            Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gcc-10   100       auto mode
  1            /usr/bin/gcc-10   100       manual mode
  2            /usr/bin/gcc-8    80        manual mode
  3            /usr/bin/gcc-9    90        manual mode

Press <enter> to keep the current choice[*], or type selection number:

```

你将会被展示一系列已经安装在你的 Ubuntu 系统上的 GCC 版本。输入你想设置为默认的 GCC 版本，并且按回车 `Enter`。

这个命令将会创建符号链接到指定版本的 GCC 和 G++。

## Z.4. 四、总结

我们已经向你演示如何在 Ubuntu 20.04 上如何安装 GCC。现在你可以浏览 [官方 GCC 文档页面](https://link.zhihu.com/?target=https%3A//gcc.gnu.org/onlinedocs/)，并且学习如何使用 GCC 和 G++ 来编译你的 C 和 C++ 程序。

如果你有任何疑问，请通过以下方式联系我们：

微信:

微信群: 加上面的微信，备注微信群

QQ: 3217680847

![](https://pic4.zhimg.com/v2-8b36b318ec0c5bd8714694806f643177_r.jpg)

QQ 群: 82695646

![](https://pic4.zhimg.com/v2-06e1fec4a87eca3142d54d09844c629f_b.png)

![](https://pic1.zhimg.com/v2-979ec26a55cfdaa35cb66ed151ef6f0c_r.jpg)