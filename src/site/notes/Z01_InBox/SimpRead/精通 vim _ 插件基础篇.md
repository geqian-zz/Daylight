---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://zhuanlan.zhihu.com/p/139847548","title":"精通 vim , 插件基础篇","summary":null,"Created-Date":"2023-08-12 08:57:17","Modified-Date":"2024-04-18 11:52:09","permalink":"/Z01_InBox/SimpRead/精通 vim _ 插件基础篇/","dgPassFrontmatter":true}
---

文章首发 **微信公众号: 「 zempty 笔记 」**

有时会收到小伙伴的私信问我 vim 的插件怎么用?  
关于这篇文章主要就是向大家介绍一下 vim 的插件应该怎么用，怎么可以快速的上手插件，和介绍几个插件的使用, 姑且做一个引子吧，vim 的插件真的是太多了，你可以针对自己的需求安装即可。

**在哪里寻找 vim 插件呢？**

1.  google 搜索，针对你的需求提炼一下关键字，找找看
2.  推荐一个插件网址：[VimOwesom](https://link.zhihu.com/?target=https%3A//vimawesome.com/) 这里拥有很多好用的插件
3.  GitHub , 去 github 上找找看，很多好用的插件这里都可以找的到
4.  知乎上找一找，有很多人分享好用的插件。  
    假如你是一个 vim 插件迷，或者有十分好用的插件，欢迎你在留言区推荐，十分感谢。

### Z.1.1. **插件管理器 vim-plug**

如果你是插件爱好者，当你使用很多插件的时候你会惊叹插件管理器真是个好东西，插件管理器有很多，也都很好用，大同小异，今天就介绍这个插件管理器 [vim-plug](https://link.zhihu.com/?target=https%3A//github.com/junegunn/vim-plug)， 有兴趣的可以点开链接访问 github 上关于这款插件的使用。  
我个人比较喜欢通过 **github 去找 vim 的插件，找到后拜读一下文档，实操一下，然后熟能生巧。。。**

**安装 vim-plug**

Unix 系统安装:

```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim


```

关于 windows 和 Neovim 使用者可以参考 [vim-plug](https://link.zhihu.com/?target=https%3A//github.com/junegunn/vim-plug) 文档相当详细。

**使用插件管理器**

无论是使用插件还是插件管理器我们都是需要配置一下 ～/.vimrc 文件的，这是 vim 中很重要的一个配置文件。  
vim 插件管理器如何安装插件呢?

例如下面介绍的四个插件 :  
[vim-startify](https://link.zhihu.com/?target=https%3A//github.com/mhinz/vim-startify)  
[nerdtree](https://link.zhihu.com/?target=https%3A//github.com/preservim/nerdtree)  
[vim-interestingwords](https://link.zhihu.com/?target=https%3A//github.com/lfv89/vim-interestingwords)  
[vim-fugitive](https://link.zhihu.com/?target=https%3A//github.com/tpope/vim-fugitive)

配置文件配置如下:

```
call plug#begin('~/.vim/plugged')

 Plug 'scrooloose/nerdtree'
 Plug 'mhinz/vim-startify' 
 Plug 'tpope/vim-fugitive' 
 Plug 'lfv89/vim-interestingwords'

call plug#end()


```

以上就是告诉插件管理器插件的地址 (以上地址均是来自 github, 地址使用作者名 / 仓库名即可)，你去帮我下载下来使用吧。  
然后在 vim 编辑器当中运行 :PlugInstall 插件就会自行安装，如下:  

![](https://pica.zhimg.com/v2-5541de5e871a92e084811dab9596c2eb.jpg?source=382ee89a)

<video src="blob:https://zhuanlan.zhihu.com/c85e9e6b-5dd1-426d-a886-27de35c44bc6" control></video>

00:00

/ 00:20

下载

播放速度

画中画

视频信息

镜像画面

循环播放

[X]

DeviceId

:

web_406665468ED7387F

PlayerVersion

:

1.0.27

SessionId

:

c3d84327-1e87-4018-8507-7b76c77c7356

StreamHost

:

vdn6.vzuu.com

Res

:

mse mp4 h264 1280x720@25.00

Color

:

(tv bt709)

Codec

:

avc1.64001f/mp4a.40.5

GPU

:

ANGLE (Intel, Intel(R) Iris(R) Xe Graphics Direct3D11 vs_5_0 ps_5_0, D3D11)

播放 (k)

00:00 / 00:20

倍速

2.0x1.5x1.25x1.0x0.75x0.5x

高清

高清 720P 清晰 480P

画中画 (p)

网页全屏 (t)

全屏 (f)

![](https://pica.zhimg.com/v2-5541de5e871a92e084811dab9596c2eb.jpg?source=382ee89a)

00:20

更新插件使用 :PlugUpdate  
更新 vim-plug 插件自己 :PlugUpgrade  
移除插件，移除配置文件的地址，执行 :PlugClean 命令即可。  
关闭插件执行界面是快捷键 q

### Z.1.2. **[nerdtree](https://link.zhihu.com/?target=https%3A//github.com/preservim/nerdtree) 插件**

我们习惯用目录，标签来操作文件，[nerdtree](https://link.zhihu.com/?target=https%3A//github.com/preservim/nerdtree) 可以展示文件所在的目录树结构和快速定为文件等，也可以使用 tag , mark 等，如下图:

![](https://pic1.zhimg.com/v2-a00c3f0fac94763c7f016528a4000bf8_r.jpg)

**使用 nerdtree**  
通常需要在 .vimrc 中配置一个出发快捷键如下:

```
 let mapleader = ","  
 nnoremap <silent> <leader>n :NERDTreeToggle<CR>


```

上述配置意思就是通过 ,n 快捷键来激活插件 nerdtree.

**使用 nerdtree 帮助文档**  
当激活 nerdtree 的时候是用 _shift +?_ 可以快速调出帮助文档，文档很简单，可以帮助我们快速的上手 nerdtree, 如下图:

![](https://pic3.zhimg.com/v2-8a84f3b5c98868e9f070ad1c40aceca2_r.jpg)

### Z.1.3. **[vim-startify](https://link.zhihu.com/?target=https%3A//github.com/mhinz/vim-startify) 插件**

这是一个使用起来非常简单的插件，方便我们浏览最近打开的文件，终端输入 vim ，我们就会进入该插件，插件的效果如下:  

![](https://pic1.zhimg.com/v2-bec34bb0e69c2eb799811e6fb5473000_r.jpg)

输入相应文件对应的数字键就可以快速打开文件了。

### Z.1.4. **[vim-interestingwords](https://link.zhihu.com/?target=https%3A//github.com/lfv89/vim-interestingwords) 插件**

有时候我们需要高亮光标处单词在文件的所有位置，该插件就有这样的功能。  
**插件应该怎么使用呢?**  
插件默认使用快捷键 ,k 来激活，激活后光标所在单词就会高亮，使用 n 或者 N 来进行下一个或者上一个高亮单词的快速的定位，有时候我们需要给高亮的不同单词不一样的颜色，可以在 .vimrc 中添加如下几行:

```
let g:interestingWordsGUIColors = ['#8CCBEA', '#A4E57E', '#FFDB72', '#FF7272', '#FFB3FF', '#9999FF']
let g:interestingWordsTermColors = ['154', '121', '211', '137', '214', '222']
let g:interestingWordsRandomiseColors = 1 


```

效果如下所示:  

![](https://pic4.zhimg.com/v2-49660de029fafbe35ef30f8e27f8da4b_r.jpg)

**关闭高亮**  
默认快捷键 ,+shift+k 也就是 , 加上大写的 K 就会快速取消所有的高亮了。

### Z.1.5. **[vim-fugitive](https://link.zhihu.com/?target=https%3A//github.com/tpope/vim-fugitive)**

这个插件是方便我们在使用 vim 的时候快速的使用 git ，提交代码在 vim 中即可实现，该插件默认不需要在配置文件当中添加任何配置即可使用。  
**这个插件怎么使用呢?**  
vim 的命令模式下输入 :Git 然后在紧跟着平时我们使用 git 的正常命令就好，例如:  
:Git status  
:Git add .  
:Git commit -am"xxxxxx"  
:Git log  
:Git push xxxx master  
正常的 git 命令使用而已，只不过 Git 首字母大写而已。  
当然这款插件为了方便也有自己独特的命令形式如:  
:GWrite  
:GRead  
:GRemove  
:GCommit  
等等。。。这些只不过简写我们的 git 命令而已，想查看具体命令的使用 :help GCommit 就可以浏览该命令的详细解释了，关于该插件的详细使用推荐阅读 [vim-fugitive](https://link.zhihu.com/?target=https%3A//github.com/tpope/vim-fugitive) 的 github 仓库的详细文档。

### Z.1.6. **总结**

vim 的插件太多，可以根据自己的需求去寻找，然后使用，就像本文一样在 github 上按需查找，然后安装，浏览一下 github 仓库中插件的详细说明，该做配置的做配置，然后实操一下，觉得好用，日常生活当中使用便可，熟能生巧，你发现你的效率再一次提高了。。。  
本文展示的插件安装的. vimrc 配置仓库 [.vimrc 配置](https://link.zhihu.com/?target=https%3A//github.com/kickcodeman/.vimrc/blob/master/.vimrc) ，在此求一波关注，期待和您成为朋友。