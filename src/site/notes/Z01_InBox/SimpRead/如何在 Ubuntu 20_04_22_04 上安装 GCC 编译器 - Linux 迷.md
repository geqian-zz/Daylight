---
{"dg-publish":true,"aliases":[null],"tags":[null],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://www.linuxmi.com/ubuntu-20-04-22-04-gcc.html","title":"如何在 Ubuntu 20.04/22.04 上安装 GCC 编译器 - Linux 迷","summary":"在本教程中，您将在 Ubuntu 20.04 /22.04 上安装 GCC 编译器。GNU Compiler C","Created-Date":"2023-08-11 09:28:42","Modified-Date":"2024-04-18 11:52:10","permalink":"/Z01_InBox/SimpRead/如何在 Ubuntu 20_04_22_04 上安装 GCC 编译器 - Linux 迷/","dgPassFrontmatter":true}
---

在本教程中，您将在 Ubuntu 20.04 /22.04 上安装 GCC 编译器。GNU Compiler Collection 主要是编译器以及 C、C++ 和 Objective-C 库的集合。

### Z.1.1. 介绍

在我们开始讨论如何在 Ubuntu 20.04/22.04 上安装 GCC 编译器之前。让我们简单了解一下 – **什么是 GCC 编译器？**

GNU Compiler Collection 主要是编译器以及 C、C++ 和 Objective-C 库的集合。有许多开源项目，例如 GNU 工具和使用 GCC 编译的 Linux 内核。

在本教程中，您将在 Ubuntu 20.04 上安装 GCC 编译器。

### Z.1.2. 先决条件

1) 您必须以 root 或具有 sudo 权限的用户身份登录。

### Z.1.3. 第 1 步 – 在 Ubuntu 上安装 GCC

1) 在这里，默认的 Ubuntu 存储库有一个元包为 `build-essential`. 它包含 GCC 编译器以及编译软件所需的许多库和实用程序。执行以下步骤在 Ubuntu 20.04/22.04 上安装 GCC 编译器。

2）首先，首先更新包列表：

```
linuxmi@linuxmi /home/linuxmi/www.linuxmi.com                                   
⚡ sudo apt-get update

```

![](https://www.linuxmi.com/wp-content/uploads/2022/04/1-1.png)

3）之后，`build-essential` 通过键入安装包：

```
linuxmi@linuxmi /home/linuxmi/www.linuxmi.com                                   
⚡ sudo apt install build-essential

```

该命令将安装一堆新软件包。它还将包括 `gcc` 和。您可能还需要安装手册页。它是关于使用 GNU/Linux 进行开发的：`g++``make`

```
linuxmi@linuxmi /home/linuxmi/www.linuxmi.com                                   
⚡ sudo apt-get install manpages-dev

```

4) 要验证 GCC 编译器的安装是否成功，您将使用 `gcc --version` 命令。它将打印 GCC 版本：

```
linuxmi@linuxmi /home/linuxmi/www.linuxmi.com                                   
⚡ gcc --version

```

5)`9.4.0` 是 Ubuntu 20.04 存储库中可用的默认 GCC 版本。

```
gcc (Ubuntu 9.4.0-1ubuntu1~20.04.1) 9.4.0
Copyright (C) 2019 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

![](https://www.linuxmi.com/wp-content/uploads/2022/04/gcc940.png)

您的系统上的 GCC 安装现已成功。您现在可以开始使用它了。

### Z.1.4. 第 2 步 – 编译 Hello World 示例

1) 要编译基本的 C 或 C++ 程序，您将使用 GCC 来完成。打开您的文本编辑器并创建以下文件：

![](https://www.linuxmi.com/wp-content/uploads/2022/04/hello.png)

2) 继续保存文件。然后，使用以下命令将其编译为可执行文件：

```
linuxmi@linuxmi /home/linuxmi/www.linuxmi.com                                   
⚡ gcc hello.c -o hello

```

3）它将 `hello` 在同一目录中创建一个具有名称的二进制文件。这是您运行命令的地方。现在，通过以下方式执行 `hello` 程序：

```
linuxmi@linuxmi /home/linuxmi/www.linuxmi.com                                   
⚡ ./hello

```

该命令将打印：

```
Linux迷 www.linuxmi.com。Hello World!

```

### Z.1.5. 

![](https://www.linuxmi.com/wp-content/uploads/2022/04/helloc.png)

### Z.1.6. 第 3 步 – 安装多个 GCC 版本

1) 在这里，您现在将在 Ubuntu 20.04 上安装和使用多个版本的 GCC。最新版本的 GCC 编译器具有新功能和优化改进。

此外，默认的 Ubuntu 存储库有多个 GCC 版本。它是从 `7.x.x` 到 `10.x.x`。现在，您将安装三个版本的 GCC 和 G++。

2) 因此，首先，`ubuntu-toolchain-r/test` 使用以下命令将 PPA 添加到您的系统中：

```
linuxmi@linuxmi /home/linuxmi/www.linuxmi.com                                   
⚡ sudo apt install gcc-8 g++-8 gcc-9 g++-9 gcc-10 g++-10

```

![](https://www.linuxmi.com/wp-content/uploads/2022/04/gcc-g.png)

3) 然后，下面的命令将为每个版本配置一个替代方案并为其关联一个优先级。默认版本是具有最高优先级的版本。这里是 `gcc-10`：

```
linuxmi@linuxmi /home/linuxmi/www.linuxmi.com                                   
⚡ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 100 --slave /usr/bin/g++ g++ /usr/bin/g++-10 --slave /usr/bin/gcov gcov /usr/bin/gcov-10
[sudo] linuxmi 的密码： 
update-alternatives: 使用 /usr/bin/gcc-10 来在自动模式中提供 /usr/bin/gcc (gcc)


```

![](https://www.linuxmi.com/wp-content/uploads/2022/04/gcc10.png)

5) 稍后如果您需要更改默认版本，您可以使用以下 `update-alternatives` 命令：

```
linuxmi@linuxmi /home/linuxmi/www.linuxmi.com                                   
⚡ sudo update-alternatives 

```

输出如下：

```
有 3 个候选项可用于替换 gcc (提供 /usr/bin/gcc)。

  选择       路径           优先级  状态
------------------------------------------------------------
* 0            /usr/bin/gcc-10   100       自动模式
  1            /usr/bin/gcc-10   100       手动模式
  2            /usr/bin/gcc-8    80        手动模式
  3            /usr/bin/gcc-9    90        手动模式

要维持当前值[*]请按<回车键>，或者键入选择的编号：

```

![](https://www.linuxmi.com/wp-content/uploads/2022/04/gccd.png)

6) 您将看到 Ubuntu 系统上所有已安装 GCC 版本的列表。然后，输入要用作默认值的版本数。继续按 `Enter`。该命令将创建指向特定版本的 GCC 和 G++ 的符号链接。

### Z.1.7. 结论

我们希望这份详细指南能帮助您在 Ubuntu 20.04 上安装 GCC 编译器。

如果您有任何疑问或疑问，请在下面的评论中留下。我们很乐意解决这些问题。