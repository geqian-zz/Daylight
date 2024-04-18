---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://blog.csdn.net/youngyangyang04/article/details/120750638","title":"人生苦短，我用 VIM！_git clone https://github.com/youngyangyang04/power_代码随想录的博客 - CSDN 博客","summary":null,"Created-Date":"2023-11-11 11:25:34","Modified-Date":"2024-04-18 11:52:11","permalink":"/Z01_InBox/SimpRead/人生苦短，我用 VIM！_git clone https：__github_com_youngyangyang04_power_代码随想录的博客 - CSDN 博客/","dgPassFrontmatter":true}
---

大家好，我是 Carl

熟悉我的录友，应该都知道我是 [vim](https://so.csdn.net/so/search?q=vim&spm=1001.2101.3001.7020) 流，无论是写代码还是写文档（Markdown），都是 vim，都没用 IDE。

但这里我并不是说 IDE 不好用，IDE 在 代码跟踪，引用跳转等等其实是很给力的，效率比 vim 高。

我用 vim 的话，如果需要跟踪代码的话，就用 ctag 去跳转，虽然很不智能（是基于规则匹配，不是语义匹配），但加上我自己的智能就也能用（这里真的要看对代码的把握程度了，哈哈哈）

所以连跟踪代码都不用 IDE 的话，其他方面那我就更用不上 IDE 了。

### Z.1.1. 为什么用 VIM

**至于写代码的效率，但 VIM 完爆 IDE**，其他不说，就使用 IDE 每次还要去碰鼠标，就很让人烦心！（真凸显了程序员的执着）

这里说一说 vim 的方便之处吧，搞后端开发的同学，都得玩 linux 吧，在 linux 下写代码，如果不会 vim 的话，会非常难受。

日常我们的开发机，线上服务器，预发布服务器，都是远端 linux，需要跳板机连上去，进行操作，如果不会 vim，每次都把代码拷贝到本地，修改编译，在传到远端服务器，还真的麻烦。

使用 VIM 的话，本地，服务器，开发机，一刀流，无缝切换，爽不。

IDE 那么很吃内存，打开个 IDE 卡半天，用 VIM 就很轻便了，秒开有木有！

而且在我们日常开发中，工作年头多了，都会发现没有纯粹的 C++，Java 开发啥的，就是 C++ 也得写，Java 也得写，有时候写 Go 起个 http 服务，写 Python 处理一下数据，写 shell 搞个自动部署，编译啥的。 **总是就是啥语言就得写，一些以项目需求为导向！**

写语言还要切花不同的 IDE，熟悉不同的操作姿势，想想是不是很麻烦。

听说好像现在有的 IDE 可以支持很多语言了，这个我还不太了解，但能确定的是，IDE 支持的语言再多，也不会有 vim 多。

**因为 vim 是编辑器！**，什么都可以写，不同的语言做一下相应的配置就好，写起来都是一样的顺畅。

应该不少录友感觉 vim 上快捷键太多了，根本记不过来，其实这和我看 IDE 是一样的想法，我看 IDE 上哪些按钮一排一排的也太多了，我都记不过来，所以索性一套 vim 流 扫遍所有代码，它不香么。

而且 IDE 集成编译、调试、智能补全、语法高亮、工程管理等等，隐藏了太多细节，使用 vim，就都自己配置，想支持什么语言就自己配置，想怎么样就怎么样，需要什么就补什么，这不是很酷么？

可能有的同学感觉什么都要自己配置，有点恐惧。但一旦配置好的就非常舒服了。

**其实工程师就要逢山开路遇水搭桥，这也是最基本的素质！**

从头打在一个自己的开发利器，再舒服不过了。

### Z.1.2. PowerVim

这里给大家介绍一下我的 vim 配置吧，**这套 vim 配置我已经打磨了将近四年**，不断调整优化，已经可以完全满足工业级打开的需求了。

所以我给它起名为 PowerVim。一个真正强大的 vim。

```
  _____                    __      ___           
  |  __ \                   \ \    / (_)          
  | |__) |____      _____ _ _\ \  / / _ _ __ ___  
  |  ___/ _ \ \ /\ / / _ \ '__\ \/ / | | '_ ` _ \ 
  | |  | (_) \ V  V /  __/ |   \  /  | | | | | | | 
  |_|   \___/ \_/\_/ \___|_|    \/   |_|_| |_| |_|

```

这个配置我开源在 Github 上，地址：https://github.com/youngyangyang04/PowerVim

**来感受一下 PowerVim 的使用体验，看起来很酷吧！**

![](https://img-blog.csdnimg.cn/img_convert/5398a3609c949ed25049c233fafded69.gif)

### Z.1.3. 安装

PowerVim 的安防非常简单，我已经写好了安装脚本，只要执行以下就可以安装，而且不会影响你之前的 vim 配置，之前的配置都给做了备份，大家看一下脚本就知道备份在哪里了。

安装过程非常简单：

```
git clone https://github.com/youngyangyang04/PowerVim.git
cd PowerVim
sh install.sh

```

### Z.1.4. 特性

目前 PowerVim 支持如下功能，这些都是自己配置的：

*   CPP、PHP、JAVA 代码补全，如果需要其他语言补全，可自行配置关键字列表在 PowerVim/.vim/dictionary 目录下
* 显示文件函数变量列表
*   MiniBuf 显示打开过的文件
* 语法高亮支持 C++ (including C++11)、 Go、Java、 Php、 Html、 Json 和 Markdown
* 显示 git 状态，和主干或分支的添加修改删除的情况
* 显示项目文件目录，方便快速打开
* 快速注释，使用 gcc 注释当前行，gc 注释选中的块
* 项目内搜索关键字和文件夹
* 漂亮的颜色搭配和状态栏显示

### Z.1.5. 最后

当然 还有很多，我还详细写了 PowerVim 的快捷键，使用方法，插件，配置，等等，都在 Github 主页的 README 上。当时我的 Github 上写的都是英文 README，这次为了方便大家阅读，我又翻译成中文 README。

![](https://img-blog.csdnimg.cn/img_convert/3df5534037e276aafeae32e0480405ce.png)

最后，因为这个 vim 配置因为我一直没有宣传，所以 star 数量很少，哈哈哈，录友们去给个 star 吧，真正的开发利器，值得顶起来！

地址：

**https://github.com/youngyangyang04/PowerVim**





---

- [[A05_Learning/A052_Vim/Vim\|Vim]]