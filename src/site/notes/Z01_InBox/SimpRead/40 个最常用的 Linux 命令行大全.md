---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://zhuanlan.zhihu.com/p/420247468","title":"40 个最常用的 Linux 命令行大全","summary":null,"Created-Date":"2023-08-11 09:31:45","Modified-Date":"2024-04-18 11:52:13","permalink":"/Z01_InBox/SimpRead/40 个最常用的 Linux 命令行大全/","dgPassFrontmatter":true}
---

在撰写本文时，Linux 在台式机上的 [全球市场份额为 2.68%](https://link.zhihu.com/?target=https%3A//www.wbolt.com/go%3F_%3Dcb1236a435aHR0cHM6Ly9ncy5zdGF0Y291bnRlci5jb20vb3MtbWFya2V0LXNoYXJlL2Rlc2t0b3Avd29ybGR3aWRl)，但超过 90% 的云基础设施和托管服务都在该操作系统中运行。仅出于这个原因，熟悉流行的 Linux 命令就至关重要。

根据 [2020 年 StackOverflow 调查](https://link.zhihu.com/?target=https%3A//www.wbolt.com/go%3F_%3De58cfedd6aaHR0cHM6Ly9pbnNpZ2h0cy5zdGFja292ZXJmbG93LmNvbS9zdXJ2ZXkvMjAyMCN0ZWNobm9sb2d5LXBsYXRmb3Jtcw%253D%253D)，Linux 是专业开发人员使用最多的操作系统，拥有令人印象深刻的 55.9% 的市场份额。这不仅仅是巧合。Linux 是免费的、开源的，比竞争对手具有更好的安全性，并且拥有强大的命令行，使开发人员和高级用户更加高效。

无论您是经验丰富的系统管理员还是 Linux 新手，都可以利用本指南。

1.  [什么是 Linux 命令？](https://link.zhihu.com/?target=https%3A//www.wbolt.com/most-used-linux-commands.html%23what-is-a-linux-command)
2.  [最常用的 Linux 命令](https://link.zhihu.com/?target=https%3A//www.wbolt.com/most-used-linux-commands.html%23the-mostused-linux-commands)
3.  [Linux 命令备忘单](https://link.zhihu.com/?target=https%3A//www.wbolt.com/most-used-linux-commands.html%23linux-commands-cheat-sheet)

### Z.1.1. 什么是 Linux 命令？

Linux 命令是在命令行上运行的程序或实用程序。命令行是一个界面，它接受文本行并将其处理为计算机的指令。

任何图形用户界面（GUI）都只是命令行程序的抽象。例如，当您通过单击 “X” 关闭窗口时，该操作后面会运行一个命令。

**标志（flag）**是我们可以向您运行的命令传递选项的一种方式。大多数 Linux 命令都有一个帮助页面，我们可以使用 `-h` 标记调用该页面。大多数情况下，标志是可选的。

**argument** 或 **parameter** 是我们给命令的输入，以便它可以正常运行。在大多数情况下，参数是一个文件路径，但它可以是您在终端中键入的任何内容。

可以使用连字符 (`-`) 和双连字符 (`--`) 调用标志，而参数的执行取决于将它们传递给函数的顺序。

### Z.1.2. 最常用的 Linux 命令

几乎每个软件工程师都需要掌握 Linux，学会 Linux，再学习其他技术就会触类旁通，更加容易，学习编程给大家推荐「知学堂」这款 APP，不仅有各种编程语言如 Python、Java、C++ 的基础语法，还有丰富的可以写入简历的实战项目，无论是职场进阶还是求职，都很适合，链接在下面了——

知乎知学堂知乎旗下职业教育平台立即听课

在开始使用最常用的 Linux 命令之前，请确保启动 **终端（terminal）**。在大多数 Linux 发行版中，您可以使用 Ctrl + Alt + T 来执行此操作。如果这不起作用，请在应用程序面板中搜索 “terminal”

![](https://pic3.zhimg.com/v2-d638a7baa6733a3103a1274bbb26347a_r.jpg)

现在，让我们一起来了解 40 个最常用的 Linux 命令。其中许多选项可以串到它们，所以请务必 [查看命令手册](https://link.zhihu.com/?target=https%3A//www.wbolt.com/go%3F_%3Df22937a542aHR0cHM6Ly9saW51eC5kaWUubmV0L21hbi8xL2Nw).

### Z.1.3. `ls` 命令

`ls` 可能是每个 Linux 用户在其终端中键入的第一个命令。它允许您列出您想要的目录的内容（默认情况下是当前目录），包括文件和其他嵌套目录。

```
ls

```

它有很多选择，所以最好使用 `--help` 来获得一些帮助。此标志返回所有可以与 ls 一起使用的 flags 参数。

例如，要着色 `ls` 命令的输出，您可以使用以下命令：

```
ls --color=auto

```

![](https://pic3.zhimg.com/v2-b54d55afdc9fc8bd0ed7658be8322c2e_r.jpg)

现在 `ls` 命令输出已着色，您可以欣赏目录和文件之间的区别。

但是，用彩色标志打字是低效的：这就是我们使用命令 `lsalias` 的原因。

### Z.1.4. `alias` 命令

`alias` 命令允许您在 shell 会话中定义临时别名。创建别名时，您指示 shell 用一系列命令替换单词。

例如，要设置 `ls` 为颜色而不每次键入标志 `--color`，您将使用：

```
alias ls="ls --color=auto"

```

正如你所看到的，`alias` 命令需要一个关键值对参数：`alias NAME="VALUE"` . 请注意，该值必须是使用引号。

如果你想列出你的 shell 会话中所有的别名，你可不使用 argument 运行命令 `alias`。

```
alias

```

![](https://pic4.zhimg.com/v2-5e0d3451a39168f52d6282d8c9fb8e33_r.jpg)

### Z.1.5. **`unalias`**命令

顾名思义，`unalias` 命令旨在从已定义的别名中删除 `alias`。要删除以前的 `ls` 别名，可以使用：

```
unalias ls

```

### Z.1.6. **`pwd`**命令

`pwd` 命令代表 “打印工作目录”，它输出您所在目录的绝对路径。例如，如果您的用户名是 “john”，并且您位于文档目录中，则其绝对路径将是 `/home/john/Documents`.

要使用它，只需在终端中键入 `pwd`：

```
pwd
# My result: /home/wbolt/Documents/linux-commands

```

### Z.1.7. **`cd`**命令

`cd` 命令与 `ls` 都非常流行。它指的是 “更改目录”，顾名思义，它会将您切换到您试图访问的目录。

例如，如果您在 Documents 目录中，并且试图访问其名为 Videos 的子文件夹之一，则可以通过键入以下内容来输入：

```
cd Videos

```

您还可以提供文件夹的绝对路径：

```
cd /home/wbolt/Documents/Videos

```

在使用 `cd` 命令时，有一些技巧可以为您节省大量时间：

**1. 进入 home 文件夹**

```
cd

```

**2. 向上移动一个级别**

```
cd ..

```

**3. 返回上一个目录**

```
cd -

```

### Z.1.8. **`cp`** 命令

直接在 Linux 终端上复制文件和文件夹非常容易，有时它可以取代传统的文件管理器。

要使用 `cp` 命令，只需将其与源文件和目标文件一起键入即可：

```
cp file_to_copy.txt new_file.txt

```

还可以使用递归标志复制整个目录：

```
cp -r dir_to_copy/ new_copy_dir/

```

请记住，在 Linux 中，文件夹以正斜杠 (`/`) 结尾。

### Z.1.9. **`rm`**命令

既然您已经知道了如何复制文件，那么了解如何删除它们将很有帮助。

您可以使用 `rm` 命令删除文件和目录。但在使用时要小心，因为用这种方法恢复删除的文件非常困难（但并非不可能）。

要删除常规文件，请键入：

```
rm file_to_copy.txt

```

如果要删除空目录，可以使用递归（`-r`）标志：

```
rm -r dir_to_remove/

```

另一方面，要删除包含内容的目录，需要使用 force（-f）和 recursive 标志：

```
rm -rf dir_with_content_to_remove/

```

警告：误用这两个标志，你可能会抹掉一整天的工作！

### Z.1.10. **`mv`**命令

您可以使用 `mv` 命令在文件系统中移动（或重命名）文件和目录。

若要使用此命令，请将其名称与源文件和目标文件一起键入：

```
mv source_file destination_folder/
mv command_list.txt commands/

```

要使用绝对路径，请使用：

```
mv /home/wbolt/BestMoviesOfAllTime ./

```

…where `./` 是您当前所在的目录。

您还可以使用 `mv` 重命名文件，同时将其保留在同一目录中：

```
mv old_file.txt new_named_file.txt

```

### Z.1.11. **`mkdir`**命令

要在 shell 中创建文件夹，可以使用 `mkdir` 命令。只需指定新文件夹的名称，确保它不存在，然后就可以开始了。

例如，要创建一个保存所有图像的目录，只需键入：

```
mkdir images/

```

要使用简单命令创建子目录，请使用 parent（`-p`）标志：

```
mkdir -p movies/2004/

```

### Z.1.12. **`man`**命令

另一个重要的 Linux 命令是 `man`。它显示任何其他命令的手册页面（只要有）。

要查看 `mkdir` 命令的手册页，请键入：

```
man mkdir

```

您甚至可以查看 `man` 命令手册页面：

```
man man

```

![](https://pic1.zhimg.com/v2-0e66d8d091daf8bd488b88d95f27eca8_r.jpg)

基础的命令只能保证您在这门技术上打好根基，如果需要在这方面有所造诣，还需要进行深度学习。比如参加知学堂 APP 的教程培训……

知乎知学堂知乎旗下职业教育平台立即听课

### Z.1.13. **`touch`**命令

`touch` 命令允许您更新指定文件的访问和修改时间。

例如，我有一个旧文件，上次修改是在 4 月 12 日：

![](https://pic2.zhimg.com/v2-80b6b2110059caaf61015be1994d408d_r.jpg)

要将其修改日期更改为当前时间，我们需要使用 `-m` 标志：

```
touch -m old_file

```

现在日期与今天的日期相符（开始编写本文时的日期为 8 月 8 日）。

![](https://pic1.zhimg.com/v2-a3e1c2b15c43519db7fa026168ea40dc_r.jpg)

尽管如此，大多数情况下，您不会使用 `touch` 来修改文件日期，而是创建新的空文件：

```
touch new_file_name

```

### Z.1.14. **`chmod`** 命令

`chmod` 命令允许您快速更改 [文件的模式](https://link.zhihu.com/?target=https%3A//www.wbolt.com/go%3F_%3D84a900dfbfaHR0cHM6Ly93aWtpLmFyY2hsaW51eC5vcmcvdGl0bGUvRmlsZV9wZXJtaXNzaW9uc19hbmRfYXR0cmlidXRlcw%253D%253D)（权限）。它有很多可用的选项。

文件的基本权限包括：

*   r (只读)
*   w (写入)
*   x (执行)

`chmod` 最常见的用例之一是使文件可由用户执行。为此，请键入 `chmod` 和标志 `+x`，然后键入要修改其权限的文件：

```
chmod +x script

```

您可以使用它使脚本可执行，从而允许您使用 `./` 符号直接运行它们。

### Z.1.15. **`./`** 命令

也许 `./` 符号本身不是命令，但在这个列表中值得一提。它允许 shell 直接从终端运行可执行文件，并在系统中安装任何解释器。不再双击图形文件管理器中的文件！

例如，使用此命令，您可以运行 Python 脚本或仅以. run 格式提供的程序，如 XAMPP。运行可执行文件时，请确保它具有可执行（x）权限，您可以使用 `chmod` 命令修改该权限。

下面是一个简单的 Python 脚本，以及如何使用 `./` 符号运行它：

```
#! /usr/bin/python3
# filename: script
for i in range(20):
print(f"This is a cool script {i}")

```

下面是我们如何将脚本转换为可执行文件并运行它：

```
chmod +x script
./script

```

### Z.1.16. **`exit`** 命令

`exit` 命令完全按照其名称执行：使用它，您可以结束 shell 会话，并且在大多数情况下，可以自动关闭正在使用的终端：

```
exit

```

### Z.1.17. **`sudo`** 命令

此命令代表 “超级用户 do”，它允许您在运行特定命令时充当超级用户或根用户。这就是 Linux 如何保护自己，防止用户意外修改机器的文件系统或安装不合适的软件包。

Sudo 通常用于安装软件或编辑用户主目录以外的文件：

```
sudo apt install gimp
sudo cd /root/

```

在运行您键入的命令之前，它会要求您输入管理员密码。

### Z.1.18. **`shutdown`** 命令

正如您可能猜到的，`shutdown` 命令允许您关闭机器电源。但是，它也可以用来停止和重新启动它。

要立即关闭计算机电源（默认为一分钟），请键入：

```
shutdown now

```

您还可以计划以 24 小时格式关闭系统：

```
shutdown 20:40

```

要取消以前的 `shutdown` 调用，可以使用 `-c` 标志：

```
shutdown -c

```

### Z.1.19. **`htop`** 命令

`htop` 是一种交互式流程查看器，可让您直接从终端管理计算机的资源。在大多数情况下，默认情况下它并没有安装，所以请确保在下载页面上 [阅读更多关于它的信息](https://link.zhihu.com/?target=https%3A//www.wbolt.com/go%3F_%3D72744a41c3aHR0cHM6Ly9odG9wLmRldi9kb3dubG9hZHMuaHRtbA%253D%253D)。

```
htop

```

![](https://pic3.zhimg.com/v2-8ddc90a537ffb33a82f955a5c04bb00e_r.jpg)

### Z.1.20. **`unzip`** 命令

**`unzip`**命令允许您从终端提取**.zip** 文件的内容。同样，默认情况下可能不会安装此软件包，因此请确保使用 package 管理器安装它。

下面命令行，指正在解压一个包含图像的. zip 文件：

```
unzip images.zip

```

### Z.1.21. `apt`, `yum`, `pacman` 命令

无论您使用的是哪个 Linux 发行版，您都可能使用 package 管理器来安装、更新和删除您每天使用的软件。

您可以通过命令行访问这些 package 管理器，并根据您的计算机运行的发行版使用其中一个或另一个 package 管理器。

以下示例将安装 [GIMP](https://link.zhihu.com/?target=https%3A//www.wbolt.com/go%3F_%3D6cb4d7c3cdaHR0cHM6Ly93d3cuZ2ltcC5vcmcv)，这是一种通常在大多数 package 管理器中可用的免费开源软件：

**1. Debian-based (Ubuntu, Linux Mint)**

```
sudo apt install gimp

```

**2. Red Hat-based (Fedora, CentOS)**

```
sudo yum install gimp

```

**3. Arch-based (Manjaro, Arco Linux)**

```
sudo pacman -S gimp

```

### Z.1.22. **`echo`** 命令

`echo` 命令在终端中显示定义的文本 - 就这么简单：

```
echo "Cool message"

```

![](https://pic1.zhimg.com/v2-0497142c525312d02cfde7d9ddcf30e8_r.jpg)

它的主要用途是在这些消息中打印环境变量：

```
echo "Hey $USER"
# Hey wbolt

```

知学堂目前已经发布了 Python、Java、C/C++、前端、大数据和人工智能等类型的课程培训，部分精选课程还是免费提供的，赶紧去深造吧！

知乎知学堂知乎旗下职业教育平台立即听课

### Z.1.23. **`cat`** 命令

**`cat`** 是 “concatenate” 的缩写，用于直接从终端创建、查看和连接文件。它主要用于在不打开图形文本编辑器的情况下预览文件：

```
cat long_text_file.txt

```

![](https://pic4.zhimg.com/v2-8877268f73c1a995d20e1247c408c51b_r.jpg)

### Z.1.24. **`ps`** 命令

使用 `ps`，您可以查看当前 shell 会话正在运行的进程。它打印有关正在运行的程序的有用信息，如进程 ID、TTY（电传打字机）、时间和命令名。

```
ps

```

![](https://pic2.zhimg.com/v2-46577dae6cdf96efc20c4f1095a08c59_r.jpg)

如果您想要更具交互性的内容，可以使用 `htop`。

### Z.1.25. **`kill`** 命令

当一个程序没有响应，并且你不能用任何方法关闭它时，这是很烦人的。幸运的是，`kill` 命令解决了这类问题。

简单地说，`kill` 向终止它的进程发送一个 TERM 或 kill 信号。

您可以通过输入 PID（进程 ID）或程序的二进制名称来终止进程：

```
kill 533494
kill firefox

```

使用此命令时要小心 - 使用 `kill` 时，可能会意外删除您正在执行的工作。

### Z.1.26. **`ping`** 命令

`ping` 是用于测试网络连接的最流行的网络终端工具。`ping` 有很多选项，但在大多数情况下，您将使用它来请求域或 IP 地址：

```
ping google.com
ping 8.8.8.8

```

### Z.1.27. **`vim`** 命令

`vim` 是一个免费的开源终端文本编辑器，从 90 年代开始使用。它允许您使用高效的键绑定编辑纯文本文件。

有些人认为使用困难——退出 VIM 是最常见的 StackOverflow 问题之一，但一旦习惯了，它就成为命令行中最好的盟友。

要启动 Vim，只需键入：

```
vim

```

![](https://pic1.zhimg.com/v2-5a0e3d0873518fab516f706128ded808_r.jpg)

### Z.1.28. **`history`** 命令

如果你正在努力记住一个命令，`history` 就会派上用场。此命令显示一个枚举列表，其中包含您过去使用过的命令：

```
history

```

![](https://pic3.zhimg.com/v2-41b85bd3a9ed4d717dcac4c7d98753d2_r.jpg)

### Z.1.29. **`passwd`** 命令

`passwd` 允许您更改用户帐户的密码。首先，它会提示您输入当前密码，然后要求您输入新密码并确认。

它类似于您在其他地方看到的任何其他密码更改，但在本例中，它直接在您的终端中：

```
passwd

```

![](https://pic3.zhimg.com/v2-39d83ab99d7714d501a33bd5495fd6f2_r.jpg)

使用时要小心 - 一不小心可能会混肴用户密码！

### Z.1.30. **`which`** 命令

`which` 命令输出 shell 命令的完整路径。如果它不能识别给定的命令，它将抛出一个错误。

例如，我们可以使用它来检查 Python 和 Brave web 浏览器的二进制路径：

```
which python
# /usr/bin/python
which brave
# /usr/bin/brave

```

### Z.1.31. **`shred`** 命令

如果您希望文件几乎无法恢复，`shred` 可以帮助您完成此任务。此命令会重复覆盖文件的内容，因此，给定的文件极难恢复。

下面是一个内容很少的文件：

![](https://pic1.zhimg.com/v2-e6f50a311bb5894005c6615bcb4d77b4_r.jpg)

现在，让我们通过键入 `shred` 命令来完成工作：

```
shred file_to_shred.txt

```

![](https://pic4.zhimg.com/v2-d726279f271f51b97546313654d5080b_r.jpg)

如果要立即删除文件，可以使用 `-u` 标志：

```
shred -u file_to_shred.txt

```

### Z.1.32. **`less`** 命令

`less`（与 [more](https://link.zhihu.com/?target=https%3A//www.wbolt.com/go%3F_%3D476aefcbf4aHR0cHM6Ly9tYW43Lm9yZy9saW51eC9tYW4tcGFnZXMvbWFuMS9tb3JlLjEuaHRtbA%253D%253D) 相反）是一个允许您前后检查文件的程序：

```
less large_text_file.txt

```

![](https://pic1.zhimg.com/v2-de9123846fb3fbe48aa38faf899746c4_r.jpg)

`less` 的优点在于它在其界面中包含了更多和 `vim` 命令。如果您需要比 `cat` 更具交互性的东西，`less` 是一个不错的选择。

学无止境。尝试在测试环境这些基础的 Linux 命令逐一体验，或者可以有更好的收获。有了这些扎实的基础之后，再学习一些在线课程，或者会有更好的，意想不到的收获哦！

知乎知学堂知乎旗下职业教育平台立即听课

### Z.1.33. **`tail`** 命令

与 `cat` 类似，`tail` 打印文件内容时有一个主要警告：它只输出最后几行。默认情况下，它打印最后 10 行，但您可以使用 `-n` 修改该数字。

例如，要打印大型文本文件的最后几行，可以使用：

```
tail long.txt

```

![](https://pic2.zhimg.com/v2-6b9f04d3ae051a4d9f4addff0983b051_r.jpg)

要仅查看最后四行，请执行以下操作：

```
tail -n 4 long.txt

```

![](https://pic2.zhimg.com/v2-c07e5db1b0da1369b2fc1c4cd3dd3ee5_r.jpg)

### Z.1.34. **`head`** 命令

这是对 `tail` 命令的补充。`head` 输出文本文件的前 10 行，但您可以使用 `-n` 标志设置要显示的任意行数：

```
head long.txt
head -n 5 long.txt

```

![](https://pic3.zhimg.com/v2-beac6d53fad8fb71a346d7e8fc2b0c5a_r.jpg)

### Z.1.35. **`grep`** 命令

Grep 是处理文本文件的最强大的工具之一。它搜索与 [正则表达式](https://link.zhihu.com/?target=https%3A//www.wbolt.com/go%3F_%3Db07cb17118aHR0cHM6Ly9yZWdleDEwMS5jb20v) 匹配的行并打印它们：

```
grep "linux" long.txt

```

您可以使用 `-c` 标志计算与给定条件匹配的次数：

```
grep -c "linux" long.txt
# 2

```

### Z.1.36. **`whoami`** 命令

该命令（who am I 的缩写）显示当前使用的 `whoami` 用户名：

```
whoami
# wbolt

```

使用 `echo` 和环境变量 $USER 可以得到相同的结果:

```
echo $USER
# wbolt

```

### Z.1.37. **`whatis`** 命令

`whatis` 打印任何其他命令的单行说明，使其成为有用的参考：

```
whatis python
# python (1) - an interpreted, interactive, object-oriented programming language
whatis whatis
# whatis (1) - display one-line manual page descriptions

```

### Z.1.38. **`wc`** 命令

Wc 代表 “字数计数”，顾名思义，它返回文本文件中的字数：

```
wc long.txt 
# 37 207 1000 long.txt

```

让我们分析一下此命令的输出：

*   37 行
*   207 字
*   1000 字节大小
* 文件名（long.txt）

如果只需要字数，请使用 `-w` 标志：

```
wc -w long.txt
207 long.txt

```

### Z.1.39. **`uname`** 命令

`uname`（Unix name 的缩写）打印可操作的系统信息，当您知道当前的 Linux 版本时，这些信息很方便。

大多数情况下，您将使用 `-a`（–all）标志，因为默认输出没有那么有用：

```
uname 
# Linux 
uname -a 
# Linux wboltmanjaro 5.4.138-1-MANJARO #1 SMP PREEMPT Thu Aug 5 12:15:21 UTC 2021 x86_64 GNU/Linux

```

### Z.1.40. **`neofetch`** 命令

[Neofetch](https://link.zhihu.com/?target=https%3A//www.wbolt.com/go%3F_%3D50202a07beaHR0cHM6Ly9naXRodWIuY29tL2R5bGFuYXJhcHMvbmVvZmV0Y2g%253D) 是一个 CLI（命令行界面）工具，它在 Linux 发行版的 ASCII 徽标旁边显示有关系统的信息，如内核版本、shell 和硬件：

```
neofetch

```

![](https://pic3.zhimg.com/v2-d17f8d0d93181576e6df6abce27664c2_r.jpg)

在大多数计算机中，此命令在默认情况下不可用，因此请确保首先使用 package 管理器安装它。

### Z.1.41. **`find`** 命令

`find` 命令根据 regex 表达式在目录层次结构中搜索文件。要使用它，请遵循以下语法：

```
find [flags] [path] -name [expression]

```

要在当前目录中搜索名为 long.txt 的文件，请输入以下命令行：

```
find ./ -name "long.txt" # ./long.txt

```

要搜索以**.py** (Python) 扩展名结尾的文件，可以使用以下命令行：

```
find ./ -type f -name "*.py" ./get_keys.py ./github_automation.py ./binarysearch.py

```

### Z.1.42. **`wget`**命令

`wget`（World Wide Web get）是从互联网检索内容的实用工具。它拥有最大的 flags 之一。

以下是您如何从 GitHub 获取一个 Python 文件：

```
wget https://raw.githubusercontent.com/DaniDiazTech/Object-Oriented-Programming-in-Python/main/object_oriented_programming/cookies.py

```

### Z.1.43. 小结

学习 Linux 可能需要一些时间，但是一旦你掌握了它的一些工具，它就成了你最好的盟友，你不会后悔选择它作为你的日常司机。

Linux 的一个显著之处在于，即使您是经验丰富的用户，您也永远不会停止学习使用它提高工作效率。

上述只是罗列了最为常见的一些 Linux 命令，要善用这些命令及学习更高阶的 Linux 知识，除了多阅读相关教程和文档外。观看知乎最新平台知学堂发布的 Linux 视频教程，或者可以实现事半功倍的效果——

知乎知学堂知乎旗下职业教育平台立即听课

P.S. 文章为翻译稿（文章转自 [40 个最常用的 Linux 命令行大全 - 闪电博 (wbolt.com)](https://link.zhihu.com/?target=https%3A//www.wbolt.com/most-used-linux-commands.html)），可能存在遗漏或者错误，见谅！

### Z.1.44. 推荐阅读

[Haiyuan Kwong：开发者必须掌握的 30 个 Git 命令行](https://zhuanlan.zhihu.com/p/637789913)[Haiyuan Kwong：Python 常见命令大全](https://zhuanlan.zhihu.com/p/566054602)[Haiyuan Kwong：数据库工程师必须掌握的 9 种 Mongodb 运算符](https://zhuanlan.zhihu.com/p/565171600)[Haiyuan Kwong：Visual Studio Code 键盘快捷键大全](https://zhuanlan.zhihu.com/p/617439313)[Haiyuan Kwong：添加 Python 注释的最佳做法有哪些？](https://zhuanlan.zhihu.com/p/604470343)